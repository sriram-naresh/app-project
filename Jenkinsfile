pipeline {
    agent any
    tools {
        jdk 'jdk'
        maven 'maven'
    }
    environment {
        registry = "sriramnaresh/dockerimage"
        registryCredentials = "dockercrends" 
    }
        
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
                    sh """
                    ' docker build -t sriramnaresh/webapp1 . '
                    """
                }
            }
        }
    }
}
