pipeline {
        agent none
        stages {
          stage("build & SonarQube analysis") {
            agent any
            
            environment {
                    SCANNER_HOME = tool 'SonarScanner'                          
                  }      
           steps {
              
              echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
                                 
              withSonarQubeEnv('SonarQube') {
                sh "$SCANNER_HOME/bin/sonar-scanner"
              }
            }
          }
          stage("Quality Gate") {
            steps {
              timeout(time: 1, unit: 'HOURS') {
                waitForQualityGate abortPipeline: true
              }
            }
          }
        }
}
