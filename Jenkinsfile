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
                dir ('/tmp/bkp') {
                   //   sh "whoami"
                      sh  "mkdir ${PORT}"
                }
            }
        }        
        stage('Creo el Container y le asigno un nombre y puerto') {
            steps {
                sh "docker run -d  --name ${NAME} -p ${PORT}:8080  -v /var/run/docker.sock:/var/run/docker.sock -v /home/bkp/${PORT}:/tmp ${IMAGTAG}"
            }
        }
        stage('SSL false') {
            steps {
                //sh "docker exec  ${NAME} cat /var/jenkins_home/secrets/initialAdminPassword"  
                sh "docker exec  ${NAME} git config --global http.sslVerify false"
           }
       } 
    }
}
