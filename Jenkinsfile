pipeline{
    agent any
    stages{
        stage('take approval') {
            steps {
                timeout(time: 1, unit: 'MINUTES') {
                    input message: 'do you want to proceed?' , ok: 'proceed'
                }
            }
        }
        
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