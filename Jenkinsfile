pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/ahmedkhan935/Lab10-11-SCD.git'
            }
        }

        stage('Dependency Installation') {
            steps {
                bat 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("my-app")
                }
            }
        }

        stage('Run Docker Image') {
            steps {
                script {
                    docker.image("my-app").run()
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
                        docker.image("my-app").push()
                    }
                }
            }
        }
    }
}