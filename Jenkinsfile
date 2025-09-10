pipeline{
    agent any
    stages{
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true // reuse the node
                }
            }
            steps{
                sh '''
                ls -l
                node --version
                npm --version
                npm install
                npm run build
                ls -l
                '''
            }
        }
    }
}