pipeline {
    agent any
    stages {
        stage('Build') {
            agent {
                sh "docker build  -t a ."
            }
        }
        stage('Levanto el Container') {
            agent {
                sh "docker run -d  --name 'a' -p 8031:8080  -v /var/run/docker.sock:/var/run/docker.sock a"
            }
        }
        stage('Veo los logs') {
            agent {
                sh "docker logs a"
            }
        }
    }
}
