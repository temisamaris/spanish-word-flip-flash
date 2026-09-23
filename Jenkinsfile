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
                sh 'npm ls vitest'
                sh 'ls -la node_modules/vitest'
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                sh 'pwd'
                sh 'ls -la'
                sh 'ls -la node_modules'
                sh 'npm ls vitest'
                sh 'npx vitest run --reporter=verbose'
            }
        }

        stage('Deploy') {
            agent {
                docker {
                    image 'alpine'
                }
            }
            steps {
                echo 'Mock deployment was successful!'
            }
        }
    }
}