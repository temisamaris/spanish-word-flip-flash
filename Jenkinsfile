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
        sh '''
            echo "===== TEST START ====="

            echo "===== PWD ====="
            pwd

            echo "===== NODE ====="
            node --version

            echo "===== NPM ====="
            npm --version

            echo "===== VITEST ====="
            npm ls vitest

            echo "===== BEFORE VITEST ====="
            echo "About to execute Vitest"

            npx vitest --version

            echo "===== AFTER VITEST VERSION ====="
            echo "Test stage continues"

        '''
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