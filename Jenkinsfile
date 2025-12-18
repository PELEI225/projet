pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/PELEI225/jenkins-docker-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-docker-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f myapp || true
                docker run -d -p 3000:3000 --name myapp jenkins-docker-app
                '''
            }
        }
    }
}
