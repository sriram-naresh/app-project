pipeline{
    agent any
    tools{
        jdk 'jdk'
        maven 'maven'
    }
    stages{
          stage(build java code')
               steps{
                    script{
                          sh """
                          mvn clean
                          mvn install
                          """
                    }
               }
          }
     }
 }
