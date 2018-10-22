#!/bin/bash
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                docker 'build  -t $IMAGETAG .'
            }
        }
        stage('Levanto el Container') {
            steps {
                docker 'run -d  --name $NAME -p $PORT:8080  -v /var/run/docker.sock:/var/run/docker.sock $IMAGETAG'
            }
        }
        stage('Veo los logs') {
            steps {
                docker 'logs $NAME'
            }
        }
    }
}
