pipeline {
    agent any

    stages {
 
        stage('Checkout Code') {
            steps {
                git branch:'main' ,
                    url: 'https://github.com/Swarnashree1309/india-state-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t india-states-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                docker stop india-container || true
                docker rm india-container || true
                docker run -d -p 8080:80 --name india-container india-states-app
                '''
            }
        }
    }
}
