pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps{
                sh '''
                ls -lh
                node --version
                npm ci
                npm run build
                ls -la
                '''
            }
        }
        stage('test'){
            steps{
                sh 'test -f build/index.html'
            }
        }
    }
}
