pipeline {
    agent any

    stages {
        stage('Checkout Repository') {
            steps {
                // Use SSH and the credentials you added in Jenkins
                git branch: 'main',
                    credentialsId: 'git-jenkins', // SSH key credential ID
                    url: 'git@github.com:credentiaagit/hello-world-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'sudo docker build -t hello-world-flask .'
            }
        }

        stage('Run Container') {
            steps {
                // Stop any existing container first
                sh 'sudo docker rm -f hello-world || true'
                // Run new container
                sh 'sudo docker run -d -p 5000:5000 --name hello-world hello-world-flask'
            }
        }
    }
}

