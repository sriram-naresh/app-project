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
                dockerImage = docker.build registry + ":$BUILD_NUMBER"
              }
            }
        }
        stage('Deploy Image') {
          steps{
            script {
              docker.withRegistry( '', registryCredential ) {
                dockerImage.push("$BUILD_NUMBER")
                dockerImage.push('latest')
              }
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
