pipeline{
    agent any
    stages{
        
        stage('Build') {
            agent {
                docker {
                    image 'node:22.11.0-alpine3.20'
                    reuseNode true // reuse the node
                }
            }
            steps{
                sh '''
                ls -l
                node --version
                npm --version
                
                '''
            }
        }
        stage('Deploy') {
            agent {
                docker {
                    image 'node:22.11.0-alpine3.20'
                    args '-u root'
                    reuseNode true
                }
            }
            steps {
                sh '''
                npm install vercel
                '''
            }
        }
        
    }
}