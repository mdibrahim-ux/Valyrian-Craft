pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/mdibrahim-ux/valyrian-craft-ci.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t valyrian-app:v1 .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker ps -q | xargs -r docker stop
                docker ps -aq | xargs -r docker rm
                docker run -d -p 80:3000 valyrian-app:v1
                '''
            }
        }
    }
}