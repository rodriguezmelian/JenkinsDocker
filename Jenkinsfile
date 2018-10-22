pipeline {
    agent none
    stages {
        stage('Build') {
            steps {
                sh "docker build  -t a ."
            }
        }
        stage('Levanto el Container') {
            steps {
                sh "docker run -d  --name 'a' -p 8031:8080  -v /var/run/docker.sock:/var/run/docker.sock a"
            }
        }
        stage('Veo los logs') {
            steps {
                sh "docker logs a"
            }
        }
    }
}
