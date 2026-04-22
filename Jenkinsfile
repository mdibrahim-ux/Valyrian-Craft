pipeline {
 agent any
 stage('Deploy Container') {
    steps {
        sh '''
        docker stop devops-container || true
        docker rm devops-container || true
        docker run -d -p 80:8080 --name devops-container devops-demo:v1
        '''
    }
}
 stages {
 stage('Build Docker Image') {
 steps { sh 'docker build -t devops-demo:v1 .' }
 }
 stage('Deploy Container') {
 steps { sh '''
 docker ps -q | xargs -r docker stop
 docker ps -aq | xargs -r docker rm
docker run -d -p 80:8080 --name devops-container devops-demo:v1
 ''' }
 }
 } }
