pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                dir('backend') {
                    script {
                        docker.build("flask-backend")
                    }
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    sh 'docker rm -f flask_app || true'
                    sh 'docker run -d -p 5000:5000 --name flask_app flask-backend'
                }
            }
        }
    }
}
