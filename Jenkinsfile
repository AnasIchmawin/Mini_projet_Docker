pipeline {
    agent any

    stages {
        stage('Cloner le Code Source') {
            steps {
                echo 'Clonage du code source...'
                    git url: 'https://github.com/AnasIchmawin/Mini_projet_Docker.git', branch: 'main'
            }
        }

        stage('Construire l\'Image Docker') {
            steps {
                echo 'Construction de l\'image Docker...'
                script {
                    dockerImage = docker.build("my-web-app:latest")
                }
            }
        }

        stage('Tester l\'Application') {
            steps {
                echo 'Test de l\'application...'
                sh 'docker run -d -p 80:80 my-web-app:latest'
                sh 'curl http://localhost'
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
}
