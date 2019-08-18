pipeline {
    agent any
    properties([
    parameters([
        string(name: 'IMAGTAG', description: 'Nombre de la imagen', ),
        string(name: 'NAME', description: 'Nombre de la imagen', ),
        string(name: 'PORT', description: 'Nombre de la imagen', ),
        string(name: 'NAME', description: 'Nombre de la imagen', )
     ])
   ])
    stages {
        stage('Build') {
            steps {
                sh "docker build  -t ${IMAGTAG} ."
            }
        }
      //  stage('Crea directorio') {
      //      steps {
      //          dir ('/tmp/bkp') {
                   //   sh "whoami"
      //                sh  "mkdir ${PORT}"
      //          }
      //      }
      //  }        
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
        stage('email'){
            steps {
              emailext(
               body:'Se adjunta archivo con la infraestructura en proceso',
               from: env.DEFAULT_REPLYTO,
               replyTo: env.DEFAULT_REPLYTO, 
               attachmentsPattern: '**/Datosimportantes.html',
               subject: 'README',
               to: "${MAIL}"        
                      )
            }
        }
    }
}
