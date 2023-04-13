pipeline {
    
    agent any
    
    tools{
        nodejs 'nodejs'
    }
    
    environment {
    scannerHome = tool 'sonarqube'
    }

    stages {
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonarqube') {
                  sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
        stage('SonarQube analysis') {
          steps {
              script{
              def scannerHome = tool 'sonarqube';
              withSonarQubeEnv('sonarqube') {
                  sh "${tool("sonarqube")}/bin/sonar-scanner \
                      -Dsonar.projectKey=NodeJs \
                      -Dsonar.projectName=NodeJs"
                  }
              }
          }
        }
        stage('Hello') {
            steps {
                sh 'npm version'
            }
        }
    }
}