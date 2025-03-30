pipeline {
    agent any

    environment {
        DOCKER_USERNAME = 'fatihmedamine'
    }

    stages {
        stage('Cloner le Code Source') {
            steps {
                echo 'Clonage du code source...'
                git branch: 'main', url: 'https://github.com/AnasIchmawin/Mini_projet_Docker.git'
            }
        }

        stage('Construire l\'Image Docker') {
            steps {
                echo 'Construction de l\'image Docker...'
                dir('aws_tp/my-web-app') {
                    script {
                        dockerImage = docker.build("${DOCKER_USERNAME}/my-web-app:latest")
                    }
                }
            }
        }

        stage('Tester l\'Application') {
            steps {
                echo 'Test de l\'application...'
                sh "docker run -d --name test-container -p 80:80 ${DOCKER_USERNAME}/my-web-app:latest"
                sh 'sleep 5'
                sh 'curl -s http://localhost:80 || exit 1'
                sh 'docker stop test-container && docker rm test-container'
            }
        }

        stage('Pousser l\'Image sur Docker Hub') {
            steps {
                echo 'Push de l\'image sur Docker Hub...'
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-credentials') {
                        dockerImage.push('latest')
                    }
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
