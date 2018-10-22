pipeline {
    agent any
    stages {
        stage('Build') {
            agent {
                docker { build  -t a .}
            }
        }
        stage('Levanto el Container') {
            agent {
                docker {run -d  --name a -p 8031:8080  -v /var/run/docker.sock:/var/run/docker.sock a}
            }
        }
        stage('Veo los logs') {
            agent {
                docker { logs a}
            }
        }
    }
}
