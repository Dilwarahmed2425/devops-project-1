pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-fresh-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop devops-fresh-container || true
                docker rm devops-fresh-container || true

                docker run -d -p 8181:80 \
                --name devops-fresh-container \
                devops-fresh-app
                '''
            }
        }
    }
}
