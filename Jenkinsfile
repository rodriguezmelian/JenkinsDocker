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
                sh "docker run -d  --name ${NAME} -p ${PORT}:8080  -v /var/run/docker.sock:/var/run/docker.sock ${IMAGTAG}"
            }
        }
        stage('SSL false') {
            steps {
                //sh "docker exec  ${NAME} cat /var/jenkins_home/secrets/initialAdminPassword"  
                sh "docker exec  ${NAME} git config --global http.sslVerify false"
           }
       } 
        stage('email Alex!'){
            emailext(
               body: 'your component is released',
               attachmentsPattern: '**/*.md',
               from: env.DEFAULT_REPLYTO,
               replyTo: env.DEFAULT_REPLYTO, 
               subject: 'README',
               to: 'rodriguezmelian@hotmail.com'
               )
            }
      } 
}
