pipeline {
    agent any
    
    stages {
      stage('Git Checkout') {
            steps {
                script {
                    git url: 'https://github.com/ramyabeemaraja/codetest1.git'
                      echo 'git checkout is done code pulled from github to jenkins workspace'
                }
            }
        }
        stage('Mvn Build') {
            steps {
                script {
                    sh 'mvn clean install'
                      echo 'maven build is done'
                }
            }
        }
        stage('docker image'){
            steps{
             
                sh 'docker build -t codetest1:${BUILD_NUMBER} -f Dockerfile .'
                echo 'docker image is created'
            }
        }
        stage('docker deploy'){
            steps{
                sh 'docker container rm -f codetest1'
                sh 'docker run --name codetest1 -itd -p 9090:9090 codetest1:${BUILD_NUMBER}'
                echo 'docker container is created'
                echo 'docker container is running'
            }
        }
        
    }
 }



