pipeline {
    agent {
        docker {
            image 'node:22-alpine'
        }
    }

    options {
        ansiColor('xterm')
    }

    stages {

        stage('Build') {
            steps {
                sh 'npm ci'
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                sh 'npx vitest run --reporter=verbose'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Mock deployment was successful!'
            }
        }
    }
}