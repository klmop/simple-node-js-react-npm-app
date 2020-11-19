pipeline {
    agent {
        docker {
            image 'node:readytalk/nodejs'
            args '-p 3000:3000'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
    }
}