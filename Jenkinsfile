pipeline {
    agent any    
    stages {
        stage('Build') {
            steps {
                sh "docker build -t your-image:f${BUILD_NUMBER} ."
            }
        }
        stage('Login to Docker Hub') {
            steps {
                withCredentials([string(credentialsId: 'dockerhub', variable: 'thevar')]) {
                    sh "docker login -u piyushdhir121 -p '${DockerHub_cred}'"
                    echo 'Login Completed'
                }
            }
        }
        stage('Push to Docker Hub') {
            steps {
                sh "docker tag your-image:e${BUILD_NUMBER} piyushdhir121/your-image:f${BUILD_NUMBER}"
                sh "dddocker push piyushdhir121/your-image:f${BUILD_NUMBER}"
                echo "Pushed to Docker Hub. Check Docker Hub for the image with tag f${BUILD_NUMBER}."
            }
        }
    }
}
