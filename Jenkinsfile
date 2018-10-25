pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh "docker build  -t ${IMAGTAG} ."
            }
        }
        stage('Creo el Container y le asigno un nombre y puerto') {
            steps {
                sh "docker run -d  --name ${NAME} -p ${PORT}:8080  -v /var/run/docker.sock:/var/run/docker.sock ${IMAGTAG}"
            }
        }
        stage('Veo los logs') {
            steps {
                sh "docker logs ${NAME} "
            }
        }
        stage('Agrego volume para backp') {
            steps {
                sh "mkdir /tmp/${PORT}"
                sh "docker run -d -v /tmp/bkp:/tmp/ ${NAME}"
            }            
        }
    }
}
