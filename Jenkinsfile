pipeline {

    agent {
        node {
            label 'AGENT-1'
        }
    }

    environment {
        COURSE = 'Jenkins'
    }

    options {
        timeout(time: 5, unit: 'MINUTES')
        disableConcurrentBuilds()
    }

    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }

    stages {

        stage('Build') {
            steps {
                sh """
                echo "Building"
                echo \$COURSE
                sleep 5
                env

                echo "Hello ${params.PERSON}"
                echo "Biography: ${params.BIOGRAPHY}"
                echo "Toggle: ${params.TOGGLE}"
                echo "Choice: ${params.CHOICE}"
                """
            }
        }

        stage('Test') {
            steps {
                sh '''
                echo "Testing"
                '''
            }
        }

        stage('Deploy') {

            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "admin"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }

            steps {
                sh '''
                echo "Deploying"
                '''
            }
        }
    }

    post {

        always {
            echo 'I will always say Hello again!'
            cleanWs()
        }

        success {
            echo 'its success!!!'
        }

        failure {
            echo 'its failure !!!'
        }

        aborted {
            echo 'pipeline is aborted'
        }
    }
}