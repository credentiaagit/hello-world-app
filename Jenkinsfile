pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/credentiaagit/hello-world-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t hello-world-flask .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 5000:5000 --name hello-world hello-world-flask || true'
            }
        }
    }
}

