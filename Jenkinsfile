pipeline {
    agent any
    tools {
        jdk 'jdk'
        maven 'maven'
    }
    stages {
        stage ("build java code"){
            steps{
                scripts{
                    sh """
                    mvn clean
                    mvn install
                    """
                }
            }
        }
    }
}