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
        
        stage('SonarQube') {
         
            steps {
                echo "SonarQube analysis starting ..."
                def scannerHome = tool 'SonarScanner 4.0';

                withSonarQubeEnv() {
                    sh "${scannerHome}/bin/sonar-scanner"
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
