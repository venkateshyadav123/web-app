pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Rakesh953/web-app.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'  
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t tomimg .'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker stop tomcat-container || true'
                sh 'docker rm tomcat-container || true'
                sh 'docker run -d -p 8081:8080 --name tomcat-container tomimg'
            }
        }
    }
}
