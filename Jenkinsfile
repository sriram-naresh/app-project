pipeline{
    agent any
    tools{
        jdk 'jdk'
        maven 'maven'
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
        stage('docker image build'){
            steps{
                script{
                    dockerImage= docker.build.sriram-naresh/appo1 + ":V$BUILD_ID "
                }
            }
        }
     }
 }
