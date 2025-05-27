pipeline {
    agent any

    environment {
        IMAGE_NAME = "node-app"
        CONTAINER_NAME = "node-app-container"
        PORT_MAPPING = "3000:3000" 
    }

    stages {
        stage('Build') {
            steps {
                echo "Building Docker image..."
                script {
                    sh "docker build -t ${IMAGE_NAME} ."
                }
            }
        }

        stage('Deploy') {
            steps {
                echo "Running Docker container..."
                script {
                    // Stop and remove existing container if exists
                    sh "docker stop ${CONTAINER_NAME} || true"
                    sh "docker rm ${CONTAINER_NAME} || true"

                    // Run new container
                    sh "docker run -d --name ${CONTAINER_NAME} -p ${PORT_MAPPING} ${IMAGE_NAME}"
                    sh "docker ps"
                    sh "curl http://localhost:3000"
                }
            }
        }
    }

    post {
        success {
            echo "Build and Run completed successfully."
        }
        failure {
            echo "Something went wrong!"
        }
    }
}
