pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
        stage('Test'){
            steps {
                sh '''
                    echo "Test stage"
                    ls -la
                    cat build/index.html
                    ls -la build/
                    npm ci
                    npm test
             '''
            }
        }
    }
}