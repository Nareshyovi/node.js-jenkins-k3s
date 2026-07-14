pipeline {

    agent any

    stages {

        stage('Clone') {
            steps {
                echo "Source code downloaded from GitHub"
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t node-app .'
            }
        }

        stage('Remove Old Container') {
            steps {
                sh '''
                docker rm -f node-container || true
                '''
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker run -d -p 3000:3000 --name node-container node-app
                '''
            }
        }

    }

}
