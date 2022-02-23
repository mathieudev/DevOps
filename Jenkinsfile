def scannerHome = tool 'sonarqube-scanner'

pipeline {
        agent none
        stages {
          stage("build & SonarQube analysis") {
            agent any
            steps {
              
              echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
                                 
              withSonarQubeEnv('SonarQube') {
                sh "${scannerHome}/bin/sonar-scanner"
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
