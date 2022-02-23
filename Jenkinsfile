pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                echo "build step"
            }
        }
        stage('test') {
            steps {
                echo "test step"
            }
        }
        
        stage('SonarQube analysis') {
            
            steps {
                withSonarQubeEnv() {
                    sh "sonar-scanner"
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
        
        stage('deploy') {
         
            steps {
             
                echo "deploy step"
            }
        }

    }
}
