pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "swelo/my-python-app:${BUILD_NUMBER}"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/swelo/Automated-CI-CD-with-Jenkins.git'

            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build(DOCKER_IMAGE)
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    docker.image(DOCKER_IMAGE).inside {
                        sh 'pytest test_app.py'
                    }
                }
            }
        }

        stage('Push to DockerHub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-credentials') {
                        docker.image(DOCKER_IMAGE).push()
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying the Docker container..."
                sh "docker run -d -p 5000:5000 ${DOCKER_IMAGE}"
            }
        }
    }
}
