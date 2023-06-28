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
                withCredentials([string(credentialsId: 'dockerhub', variable: 'dockerhubCred')]) {
                    sh "docker login -u piyushdhir121 -p '${dockerhubCred}'"
                    echo 'Login Completed'
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                sh "docker tag your-image:f${BUILD_NUMBER} piyushdhir121/your-image:f${BUILD_NUMBER}"
                sh "docker push piyushdhir121/your-image:f${BUILD_NUMBER}"
                echo "Pushed to Docker Hub. Check Docker Hub for the image with tag f${BUILD_NUMBER}."
            }
        }
    }
}
