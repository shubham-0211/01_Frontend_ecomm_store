pipeline {
    agent any

    stages {
        stage('Git clone') {
            steps {
               git branch: 'main', url: 'https://github.com/shubham-0211/01_Frontend_ecomm_store.git'
            }
        }
        
        stage('Docker Image'){
            steps{
                sh 'docker build -t shubhamghongade/ecomm_store .'
            }
        }
        
       stage('Docker Image push'){
            steps{
            withCredentials([string(credentialsId: 'docker_pwd', variable: 'docker_pwd')]) {
                   sh 'docker login -u ashokit -p ${docker_pwd}'
                   sh 'docker push shubhamghongade/ecomm_store'
            }
            }
        }
        
         stage('k8s deployment'){
            steps{
             sh 'kubectl apply -f Deployment.yml'
            }
        }  
        
        
    }
}
