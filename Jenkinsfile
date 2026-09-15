pipeline  {
    agent any 
    parameters {
        choice(name: 'ENVIRONMENT', choices: ['staging', 'production'], description: 'Target')
    }
    stages {
        stage('build') { steps { sh  'echo building'}}
