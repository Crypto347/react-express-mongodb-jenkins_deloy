pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                checkout scm // Lấy mã nguồn từ repository
            }
        }

        stage('Build Docker Images') {
            steps {
                script {
                    sh 'docker-compose down' // Dừng các container cũ
                    sh 'docker-compose build' // Build các images từ Dockerfile
                }
            }
        }

        stage('Deploy Services') {
            steps {
                script {
                    sh 'docker-compose up -d' // Chạy các container
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                script {
                    sh 'docker ps' // Kiểm tra các container đang chạy
                }
            }
        }
    }
}
