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
        // Timeout counter starts AFTER agent is allocated
        timeout(time: 10, unit: 'SECONDS')
        disableConcurrentBuilds()
    }

    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    // this is build section //
    stages {
        stage('Build') {
            steps {
                script{
                        sh """
                        echo "Building"
                        echo \$COURSE
                        sleep 5
                        env

                        echo "Hello ${params.PERSON}"
                        echo "Biography: ${params.BIOGRAPHY}"
                        echo "Toggle: ${params.TOGGLE}"
                        echo "Choice: ${params.CHOICE}"
                        echo "Password: ${params.PASSWORD}"
                        """
                }
               
            }
        }
        stage('Test') {
            steps {
                 script{
                        sh """ 
                        echo "Testing"
                        """
                }
            }
        }
        stage('Deploy') {
            steps {
                 script{
                        sh """ 
                        echo "Deploying"
                        """
                }
            }
        }
    }

     post { 
        always { 
            echo 'I will always say Hello again!'
            cleanWs()
        }
        success{
                 echo 'its success!!!'   
        }
        failure{
                echo 'its failure !!!'
        }
       aborted {
                echo 'pipeline is aborted'
            }
    }


}