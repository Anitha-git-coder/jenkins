pipeline {
    agent {
        node {
        label 'AGENT-1'
       }
    }
    stages {
        stage('Build') {
            steps {
                script{
                        sh """ 
                        echo "Building-1"
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
    }


}