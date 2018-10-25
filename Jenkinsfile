pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh "docker build  -t ${IMAGTAG} ."
            }
        }
        stage('Crea directorio') {
            steps {
                dir ('/tmp') {
                      sh  "mkdir ${PORT}"
                }
            }
        }        
        stage('Creo el Container y le asigno un nombre y puerto') {
            steps {
                sh "docker run -d  --name ${NAME} -p ${PORT}:8080  -v /var/run/docker.sock:/var/run/docker.sock -v /tmp/${PORT}:/tmp ${IMAGTAG}"
            }
        }
        stage('Veo los logs') {
            steps {
                sh "docker container exec -it ${NAME} git config --global http.sslVerify false"  
            }
        }
    }
}
