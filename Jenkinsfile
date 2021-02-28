pipeline {
   
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
                 sh 'docker push myassignment.jfrog.io/docker-local/docker-local:assignment_0227'     
            }
        }
    }
}