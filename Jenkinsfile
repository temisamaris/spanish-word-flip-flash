pipeline {
    agent any
    
    options {
        ansiColor('xterm')
    }

    stages {
        stage('build') {
            agent {
                docker {
                    image 'node:22-alpine'
                }
            }
            steps {
                sh 'npm ci'
                sh 'npm ls vitest'
                sh 'ls -la node_modules/vitest'
                sh 'npm run build'
}
        }

        stage('test') {
    parallel {
        stage('unit tests') {
            agent {
                docker {
                    image 'node:22-alpine'
                    reuseNode true
                }
            }
            steps {
                sh 'pwd'
                sh 'ls -la'
                sh 'ls -la node_modules || true'
                sh 'npm ls vitest || true'
                sh 'npx vitest run --reporter=verbose'
            }
        }
    }
}

        stage('deploy') {
            agent {
                docker {
                    image 'alpine'
                }
            }
            steps {
                // Mock deployment which does nothing
                echo 'Mock deployment was successful!'
            }
        }
    }
}