pipeline {
    agent any

    stages {
        stage('Test') {
            when {
                branchName 'main'
            }
            steps {
                sh 'echo Running tests'
            }
        }
    }
}
