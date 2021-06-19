pipeline{
    agent any
    tools{
        jdk 'jdk'
        maven 'maven'
    }
    environment{
        registry ="sriramnaresh/java-image"
        registryCrendentail ="dockercrends"
    }
    stages{
        stage("build java code"){
               steps{
                    script{
                          sh """
                          mvn clean
                          mvn install
                          """
                    }
               }
        }
        stage('bild code test'){
            steps{
                script{
                    sh """
                    mvn test
                    """
                }
            }
        }
        stage('Building image') {
            steps{
              script {
                  sh 'docker build -t  sriramnaresh/java-image . '
              }
            }
        }
        stage('Deploy Image') {
          steps{
            script {
              withCredentials([usernameColonPassword(credentialsId: 'dockercrends', variable: 'dockercrends')]) {
                  sh "docker login -u sriramnaresh -p ${dockercrends}"
              }
               sh ' docker push sriramnaresh/java-image'
            }
          }
        }
        stage('Remove Unused docker image') {
          steps{
            sh "docker rmi $registry:$BUILD_NUMBER"
          }
        }
     }
 }
