pipeline {
    agent any
 
    triggers {
        pollSCM('* * * * *')  // Poll SCM every minute
    }
 
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
 
        stage('Build and Test') {
            steps {
                // Your common build and test steps here
            }
        }
 
        stage('Deploy Microservice A') {
            when {
                changeset '**/microserviceA/**'
            }
            steps {
                // Deployment steps for Microservice A
            }
        }
 
        stage('Deploy Microservice B') {
            when {
                changeset '**/microserviceB/**'
            }
            steps {
                // Deployment steps for Microservice B
            }
        }
 
        // Add more stages for other microservices as needed
 
    }
 
    post {
        success {
            echo 'Build and tests passed. Ready for deployment.'
        }
 
        failure {
            echo 'Build or tests failed. Deployment skipped.'
        }
    }
}
