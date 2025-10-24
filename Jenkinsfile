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
    }
}
