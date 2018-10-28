pipeline {
    agent any
    stages {
        stage('email'){
            steps {
              emailext(
               body:""" <p>
               Tus ambientes de CI se estan creando en estos mommentos:
               Gitlab: 
                    Ingresas con tu cuenta de Active Directory (Gestionada con Seguridad Informacion INT - 0909) <br>
                    "<a href=https://gitab-it.gscorp.ad </a>"<br>
                    Agrega la siguiente llave para poder conectarte por ssh desde Jekins<br>
                    <br>
                    
               Jenkins:<br>
                    Vas a contar con un container de Jenkins con Docker CE.<br>
                    En breve recibiras un mail con el link mas las credenciales <br>
                    Para la conexion con Gitlab ya vas a tener la credencial condigurada con la <br>
                    PrivateKey correspondiente.<br>
               Registry: <br>
                    Azure: Utiliza la siguientes credenciales y comandos para realizar push y pull.<br>
                </p>""",
               from: env.DEFAULT_REPLYTO,
               replyTo: env.DEFAULT_REPLYTO, 
               attachmentsPattern: '**/report.html',
               subject: 'README',
               to: 'rodriguezmelian@hotmail.com'
               )
            }
        }
    }
}
