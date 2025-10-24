pipeline {
    agent any 
    tools {
        maven 'mymaven'
    }
    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/Sonal0409/DevOpsCodeDemo.git'
            }
        }
        stage('Compile Code') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('Package Code') {
            steps {
                sh 'mvn package'
            }
        }
        stage('build image'){
            steps{
                sh 'docker build -t myaddressbook .'
            }
        }
        stage('push image'){
            steps{
                withCredentials([string(credentialsId: 'PASS', variable: 'DOCKER_HUB_PASSWD')]) {
                    sh 'docker login-u harshraisaxena -p ${DOCKER_HUB_PASSWD}'
                    sh 'docker tag myaddressbook harshraisaxena/myaddressbook'
                    sh 'docker push harshraisaxena/myaddressbook'
                }
            }
        }
        stage ('deploy the container'){
            steps{
                sh 'docker run -d -P harshraisaxena/myaddressbook'
            }
        }
    }
}
