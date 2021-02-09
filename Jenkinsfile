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
                 sh "docker build -t cr33dx/nanop:$env.BUILD_ID -t cr33dx/nanop:latest ."
            }
        }
        stage("Docker Push") {
            steps {
                sh "docker push cr33dx/nanop:latest && docker push cr33dx/nanop:$env.BUILD_ID"                
            }
        }
//        stage("Update Deployment"){
//            steps{
//                sh "KUBECONFIG=/etc/kube/staging kubectl set image cronjob/scraper scraper=cr33dx/greendeck:$env.BUILD_ID
//           }        
//        }        
    }
}
