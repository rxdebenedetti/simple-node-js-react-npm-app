pipeline {
    agent {
        docker {
            image 'node:6-alpine' 
            args '-p 3004:3000' 
        }
    }
    environment { 
         CI = 'true'
    }
    stages {
        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }
        stage('Test') { 
            steps {
                sh './jenkins/scripts/test.sh' 
            }
        }
        stage('Deploy') { 
            steps {
                sh './jenkins/scripts/deliver.sh' 
                input 'continuar?'
            }
        }
    }
}
