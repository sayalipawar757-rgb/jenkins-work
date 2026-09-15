pipeline {
    agent any

    parameters {
        string(
            name: 's1',
            defaultValue: 'abcd',
            description: 's1 to deploy'
        )

        choice(
            name: 'ch',
            choices: ['staging', 'production'],
            description: 'Target'
        )

        booleanParam(
            name: 'bparam',
            defaultValue: false,
            description: 'Skip tests'
        )
    }

    stages {
        stage('build') {
            steps {
                echo "building"
            }
        }
    }
}
