pipeline {
    agent any 
    stages {
        stage('Test') {
            steps {
                sh 'echo Runnning Tests'
            }
        }
        stage('Approve') {
            steps {
                input message: 'test passed. depoly to production'
            }
        }
        stage('Deploy') {
            steps {
                sh 'deploying'
            }
        }
    }
}

            
                    
                          
