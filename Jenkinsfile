pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh 'docker build -t html-website .'
            }
        }

        stage('Run') {
            steps {
                sh 'docker rm -f test-container || true'
                sh 'docker run -d -p 9090:80 --name test-container html-website'
            }
        }

        stage('Test') {
            steps {
                sh 'curl -f http://localhost:9090'
            }
        }

        stage('Deploy') {
            steps {
                sh 'echo "Deployment successful 🚀 Access app at http://localhost:9090"'
            }
        }
    }
}
