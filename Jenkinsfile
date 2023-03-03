pipeline {
    agent any
    environment{
        DOCKERHUB_CREDS = credentials('dockerHub')
    }
    stages{
        stage('Code'){
            steps{
                checkout scm
                sh 'ls *' 
            }
        }
        stage('Build and Test'){
            steps{
                sh 'docker build . -t souravdeveloper/node-todo-test:latest'
            }
        }
        stage('Push'){
            steps{
                 
        	     sh 'echo $DOCKERHUB_CREDS_PSW | docker login -u $DOCKERHUB_CREDS_USR --password-stdin'     
                 sh 'docker push souravdeveloper/node-todo-test:latest'
                
            }
        }
    }
}
