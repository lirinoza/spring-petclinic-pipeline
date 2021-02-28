pipeline {
   
   environment { 
3       registry = "myassignment.jfrog.io/docker-local" 
4       registryCredential = 'JfrogAws_Id' 
5   
    }
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn test'
                }
            }
        }

        stage('Maven Install') {
            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn package -DskipTests'
                }
                
            }
        }
        stage('Docker Build') {
           
            steps {
                 sh 'docker build -t myassignment.jfrog.io/docker-local/docker-local:assignment_0227 .'
            }
        }
        stage('Publish Docker Image') {
           
            steps {
                docker.withRegistry( '', registryCredential ) { 
                    sh 'docker push myassignment.jfrog.io/docker-local/docker-local:assignment_0227'    
                } 
            }
        }
    }
}