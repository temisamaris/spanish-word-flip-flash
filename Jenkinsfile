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
            parallel {
                stage('unit tests') {
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
            }
        }

        stage('Deploy') {
            agent {
                docker {
                    image 'alpine'
                    reuseNode true
                }
            }
            steps {
                echo 'Mock deployment was successful!'
            }
        }
    }
}