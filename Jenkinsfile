pipeline {
    agent any

    environment {
        IMAGE_NAME = "calculator"
        DOCKERHUB_USER = "benhur167"
    }

    stages {

        stage('Build Docker Image') {
            steps {
                bat "docker build -t %DOCKERHUB_USER%/%IMAGE_NAME% ."
            }
        }

        stage('Clean Old Container') {
            steps {
                bat "docker stop calculator-app || exit 0"
                bat "docker rm calculator-app || exit 0"
            }
        }

        stage('Run Container') {
            steps {
                bat "docker run -d -p 3000:3000 --name calculator-app %DOCKERHUB_USER%/%IMAGE_NAME%"
            }
        }

    }
}
