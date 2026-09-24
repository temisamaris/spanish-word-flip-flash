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
            parallel {
                stage('Unit tests') {
                    agent {
                        docker {
                            image 'node:22-alpine'
                            reuseNode true
                        }
                    }
                    steps {
                        sh 'npx vitest run --reporter=verbose'
                    }
                }
                stage('Integration tests'){
                    agent{
                        docker{
                            image 'mcr.microsoft.com/playwright:v1.54.2-jammy'
                            reuseNode true
                        }
                    }
                    steps{
                        sh 'npx playwright test'
                    }
                }
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