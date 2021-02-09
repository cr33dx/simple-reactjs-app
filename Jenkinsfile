pipeline {
    agent any
    stages {
      stage('Checkout') {
        steps {
          checkout scm
        }
      }
        stage("Docker Build") {
            steps {
                 sh "sudo docker build -t cr33dx/nanop:$env.BUILD_ID -t cr33dx/nanop:latest ."
            }
        }
        stage("Docker Push") {
            steps {
                sh "sudo docker push cr33dx/nanop:latest && sudo docker push cr33dx/nanop:$env.BUILD_ID"                
            }
        }
        stage("Update Deployment"){
            steps{
                sh "kubectl set image deploy/react-app react-app=cr33dx/nanop:$env.BUILD_ID"
           }        
       }        
    }
}
