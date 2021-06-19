pipeline{
    agent any
    tools{
        JDK 'jdk'
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
