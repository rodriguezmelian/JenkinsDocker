pipeline {
    agent any
    stages {
        stage('email'){
            steps {
              emailext(
               body:'Se adjunta archivo con la infraestructura en proceso',
               from: env.DEFAULT_REPLYTO,
               replyTo: env.DEFAULT_REPLYTO, 
               attachmentsPattern: '**/report.html',
               subject: 'README',
                  to: '${MAIL}'
               )
            }
        }
    }
}
