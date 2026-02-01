pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/anu-rb06/fun-lab.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build --no-cache -t funlab-image .'
            }
        }

        stage('Run Container') {
            steps {
                echo 'Running container...'
                sh '''
                docker stop funlab || true
                docker rm funlab || true
                docker run -d --name funlab -p 8081:8080 funlab-image
                '''
            }
        }
    }
}
