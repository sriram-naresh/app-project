pipeline{
    agent any
    tools{
        jdk 'jdk'
        maven 'maven'
    }
    environment{
        registry ="sriramnaresh/java-image"
        registryCrendentail ="dockercrends"
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
        stage('docker image build'){
            steps{
                script{
                    sh ' docker build -t sriram-naresh/java-image .'
                }
            }
        }
        stage("push images"){
            steps{
                script{
                    docker.withRegistry ("registryCrendials"){
                        dockerImage.push ("V$BUILD_ID")
                    }
                }
            }
        }
        stage("deleted unsage"){
            steps{
                script{
                    sh "docker rmi $registry:V$BUILD_ID"
                }
            }
        }
     }
 }
