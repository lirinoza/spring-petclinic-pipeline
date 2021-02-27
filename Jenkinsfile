pipeline {
    environment { 
3
        registry = "lirinassignment/lirinassignment_0227" 
4       registryCredential = 'dockerhub_id' 
5       dockerImage = '' 
6  }
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
                 sh 'docker build -t lirinoza/spring-petclinic:latest .'
            }
        }
        stage('Publish Docker Image') {
           
            steps {
                docker.withRegistry( '', registryCredential ) { 
                 sh 'docker push lirinoza/spring-petclinic:latest'
                }
            }
        }
    }
}