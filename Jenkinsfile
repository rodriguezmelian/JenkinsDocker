#!/bin/bash
pipeline

{
    agent any
    stages{
        
            stage('Compilacion')
		{
			agent {
				docker { 'build  -t $IMAGETAG .'
				}
    {
			agent {
				docker { 'run -d  --name $NAME -p $PORT:8080  -v /var/run/docker.sock:/var/run/docker.sock $IMAGETAG'
				}
			}
    {
			agent {
				docker { 'docker logs $NAME'
				}
			}					
    }
}
