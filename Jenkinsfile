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
                    sh ' docker build -t sriram-naresh/java-image .'
                }
            }
        }
     }
 }
