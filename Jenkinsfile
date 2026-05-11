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
    stages {
        stage('Build') {
            steps {
                script{
                        sh """ 
                        echo "Building-1"
                        echo $COURSE
                        sleep 10
                        env
                        """
                }
               
            }
        }
        stage('Test') {
            steps {
                 script{
                        sh """ 
                        echo "Testing-1"
                        """
                }
            }
        }
        stage('Deploy') {
            steps {
                 script{
                        sh """ 
                        echo "Deploying-1"
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
                 echo 'its success'   
        }
        failure{
                echo 'its failure'
        }
        aborted{
            echo 'pipeline is abouted'
        }
    }


}