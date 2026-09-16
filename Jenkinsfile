```
pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh './build.sh'
            }
        }

        stage('Test') {
            when {
                anyOf {
                    branch 'main'
                    branch 'dev'
                }
            }
            steps {
                sh './test.sh'
            }
        }

        stage('Approval') {
            when {
                branch 'main'
            }
            steps {
                input message: 'Approve deployment?'
            }
        }

        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                sh './deploy.sh'
            }
        }
    }
}
```
