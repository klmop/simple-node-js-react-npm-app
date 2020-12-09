pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000'
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
        stage('Test - 1') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                echo "Running ${env.BUILD_ID} on ${env.NODE_NAME}"
                input message: 'Voulez-vous continuer le build? (Cliquer sur "Continuer" pour continuer)'
                sh './jenkins/scripts/deliver.sh'
            }
        }
    }
}