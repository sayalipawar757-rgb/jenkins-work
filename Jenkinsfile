pipeline {
    agent any

    stages {
        stage('Test') {
            when {
                branch'main'
            }
            steps {
                sh 'echo Running tests'
            }
        }
    }
}
