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
                sh 'mvn package -DskipTests'
            }
        }
        stage('Docker Build') {
           
            steps {
                 sh 'docker build -t lirinoza/spring-petclinic:latest .'
            }
        }
    }
}