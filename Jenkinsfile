pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/3012akash/devops-training-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-training-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker stop mycontainer || true
                docker rm mycontainer || true
                '''
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker run -d \
                -p 8082:80 \
                --name mycontainer \
                devops-training-app
                '''
            }
        }

    }
}
