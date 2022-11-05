def dockerimage
pipeline {
    
     agent any
    
  tools {nodejs "NodeJS 18.4.0"}
    stages {
        
        stage('Deployer app node'){

          steps {
           echo 'test'
          }
        }
        
        stage('Build') {
          steps {
            sh 'npm i nohup -g'  
            sh 'npm --version'  
            sh 'npm install express'
            sh 'npm install mongo'
            sh 'npm install mocha -g'
            
          }
        }  
        /* stage('Test') {
          steps {
            sh 'npm test'
          }
        }*/
        stage('Build image with docker') {
             steps{
                script{
                   
                   dockerImage = docker.build("yaouini/appnode-oct:latest")
                    
                }
             }
                    
          }
        stage('Push image') {
            steps{
                script{
           
                    withDockerRegistry([credentialsId: "docker-hub", url:""]){
                    dockerImage.push()
                    
              }
               }
             }
        }
        
        
        /*stage('Docker Build and Push'){
            steps{
                withDockerRegistry([credentialsId: "docker-hub", url:""]){
                    //sh 'printenv'
                    sh 'docker build -t yaouini/appnode-oct:""$GIT_COMMIT"" .'
                    sh 'docker push yaouini/appnode-oct:""$GIT_COMMIT"" '
                }
            }
            
        }*/
        
         
        
    }
}
