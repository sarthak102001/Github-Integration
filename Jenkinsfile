pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Build the code using Maven
                sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                // Run unit tests
                sh 'mvn test'
                // Run integration tests
                sh 'mvn integration-test'
            }
        }
        stage('Code Analysis') {
            steps {
                // Analyze code using Jenkins built-in tools like Checkstyle, PMD, FindBugs
                // Example: sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('Security Scan') {
            steps {
                // Perform security scan using a tool like OWASP ZAP or SonarQube
                // Example: sh 'docker run -v <your_code_directory>:/zap/wrk/:rw -t owasp/zap2docker-stable zap-full-scan.py -t http://localhost:8080'
            }
        }
        stage('Deploy to Staging') {
            steps {
                // Deploy to staging server using a tool like AWS CodeDeploy
                // Example: sh 'aws deploy create-deployment --application-name <your_application_name> --deployment-group-name <your_deployment_group_name> --s3-location <your_s3_location>'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                // Run integration tests on staging environment
                // Example: sh 'java -jar selenium-server-standalone.jar'
            }
        }
        stage('Deploy to Production') {
            steps {
                // Deploy to production server using a tool like AWS CodeDeploy
                // Example: sh 'aws deploy create-deployment --application-name <your_application_name> --deployment-group-name <your_deployment_group_name> --s3-location <your_s3_location>'
            }
        }
    }
    
    post {
        always {
            // Send email notification with attachment
            emailext attachLog: true, to: 'sarthaksharma084@gmail.com', subject: "Pipeline ${currentBuild.result}: ${env.JOB_NAME}", body: "Pipeline ${currentBuild.result}: ${env.JOB_NAME}"
        }
    }
