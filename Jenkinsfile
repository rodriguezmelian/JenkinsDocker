pipeline {
    agent any
    stages {
        stage('Build') {
            agent {
                docker { build  -t $IMAGETAG .}
            }
        }
        stage('Levanto el Container') {
            agent {
                docker {run -d  --name $NAME -p $PORT:8080  -v /var/run/docker.sock:/var/run/docker.sock $IMAGETAG}
            }
        }
        stage('Veo los logs') {
            agent {
                docker { logs $NAME}
            }
        }
    }
}
