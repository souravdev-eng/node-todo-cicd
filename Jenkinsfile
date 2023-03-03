pipeline {
    agent any
    environment{
        DOCKERHUB_CREDS = credentials('dockerHub')
    }
    stages{
        stage('Code'){
            steps{
                git url: 'https://https://github.com/souravdev-eng/node-todo-cicd.git', branch: 'master' 
            }
        }
        stage('Build and Test'){
            steps{
                sh 'docker build . -t souravdeveloper/node-todo-test:latest'
            }
        }
        stage('Push'){
            steps{
                 withDockerRegistry([ credentialsId: "dockerHub", url: "" ]) {
        	      sh 'echo $DOCKERHUB_CREDS_PSW | docker login -u $DOCKERHUB_CREDS_USR --password-stdin'     
                 sh 'docker push souravdeveloper/node-todo-test:latest'
                }
            }
        }
    }
}
