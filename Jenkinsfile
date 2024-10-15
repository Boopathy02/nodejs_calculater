pipeline {
    agent any 
    environment {
        docker_image_name = 'nodejs_calculater'
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'git@github.com:vanthiyadhevan/nodejs_calculater.git', branch: 'main', credentialsId: 'vanthiyadhevan'
            }
        }
        stage('Install Dependency') {
        	steps {
        		sh 'npm install -g @angular/cli'
        	}
        }
        stage('Build') {
            steps {
                sh 'ng build'
            }
        }
        stage('Test') {
            steps {
                sh 'ng test'
            }
        }
        stage('Test E2E') {
            steps {
                sh 'ng e2e'
            }
        }
        stage('Build As Docker Image') {
            steps {
                script {
                    docker.build("${docker_image_name}:${BUILD_NUMBER}", "Dockerfile")
                }
            }
        }
    }
}
