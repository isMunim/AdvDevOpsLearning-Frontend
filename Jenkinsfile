pipeline {
    agent any 
    environment {
        registryCredential = 'docker'
        imageName = 'ismunim/nodejs-backend:v1.'
        dockerImage = ''
        }
    stages {
        stage('Setting Up') {
             agent {
                docker { 
                    image 'node:14-alpine'
                    args '-e HOME=/tmp -e NPM_CONFIG_PREFIX=/tmp/.npm'
                    reuseNode true
                }
            }
            steps {
                echo 'Retrieve source from github. run npm install and npm test'
                git branch: 'master',
                    url: 'https://github.com/isMunim/AdvDevOpsLearning-Frontend.git'
                echo 'checking if that worked'
                sh 'ls -a'
                sh 'npm install'
                sh 'npm test'
            }
        }
        // stage('Building image') {
        //     steps{
        //         script {
        //             echo 'build the image' 
        //         }
        //     }
        //     }
        // stage('Push Image') {
        //     steps{
        //         script {
        //             echo 'push the image to docker hub' 
        //         }
        //     }
        // }     
        //  stage('deploy to k8s') {
        //      agent {
        //         docker { 
        //             image 'google/cloud-sdk:latest'
        //             args '-e HOME=/tmp'
        //             reuseNode true
        //                 }
        //             }
        //     steps {
        //      }
        // }     
        // stage('Remove local docker image') {
        //     steps{
        //         sh "docker rmi $imageName:latest"
        //         sh "docker rmi $imageName:$BUILD_NUMBER"
        //     }
        // }
    }
}