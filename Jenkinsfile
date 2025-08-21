pipeline {
    agent any

    stages {
        stage('build') {
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
        stage(" test stage"){
            steps {
                sh '''
                    ls -l
                    test -f build/index.html
                    echo "hello from test stage"
                '''
            }
        }
    }
}
