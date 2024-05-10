pipeline {
    agent any
    environment {
        DIRECTORY_PATH = "/path/to/code"
        TESTING_ENVIRONMENT = "test-env"
        PRODUCTION_ENVIRONMENT = "production-env"
    }
    stages {
        stage('Build') {
            steps {
                echo "I am fetching the source code from: ${env.DIRECTORY_PATH} using Maven"
                echo "I am compiling the code and generating output"
                // Maven build steps go here
            }
        }
        stage('Unit and Integration Test') {
            steps {
                echo "Ran unit tests"
                sleep(time: 10, unit: 'SECONDS')
                echo "I am running integration tests"
                // Test steps go here
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Integrated a code analysis tool to analyze the code using SonarQube"
                // SonarQube analysis steps go here
            }
        }
        stage('Security Scan') {
            steps {
                echo "I am performing security scan using OWASP ZAP"
                // OWASP ZAP scan steps go here
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "I am deploying the application to a staging server in AWS Elastic Beanstalk"
                // Deployment to staging steps go here
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                echo "I am running integration tests on the staging environment"
                // Integration tests on staging steps go here
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "I am deploying the code to production environment: ${env.PRODUCTION_ENVIRONMENT}"
                // Deployment to production steps go here
            }
        }
    }
    
    post {
        success {
            // Send notification email for successful pipeline
            emailext (
                subject: "Pipeline Status: SUCCESS",
                body: "The Jenkins pipeline has completed successfully.",
                to: "sarthaksharma084@gmail.com",
                mimeType: 'text/html',
                attachLog: true
            )
        }
        failure {
            // Send notification email for failed pipeline
            emailext (
                subject: "Pipeline Status: FAILURE",
                body: "The Jenkins pipeline has failed.",
                to: "sarthaksharma084@gmail.com",
                mimeType: 'text/html',
                attachLog: true
            )
        }
    }
}
