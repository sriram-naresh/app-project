pipeline {
    agent any
    tools {
        Jdk 'jdk'
        maven 'maven'
    }
    environment {
        registry = "sriramnaresh/dockerimage"
        registryCredentials = "dockercrends" 
        
    stages {
        stage ("build java code"){
            steps{
                script{
                    sh """
                    mvn clean
                    mvn install
                    """
                }
            }
        }
        stage ("build images") {
            steps{
                script{
                    dockerImage = docker.build registry + "v$BUILD_ID"
                }
            }
        }
                    
    }
}
