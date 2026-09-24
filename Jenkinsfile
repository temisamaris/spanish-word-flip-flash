pipeline {
    agent any

    options {
        ansiColor('xterm')
    }

    stages {

        stage('Build') {
            agent {
                docker {
                    image 'node:22-alpine'
                }
            }
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