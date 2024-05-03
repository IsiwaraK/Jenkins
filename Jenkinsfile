pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven...'
                // Run Maven to build the code
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests...'
                // Run unit tests using JUnit or TestNG
                // Tool: JUnit, TestNG
                
                echo 'Running integration tests...'
                // Run integration tests using Selenium or Cucumber
                // Tool: Selenium, Cucumber
            }
             post {
                success {
                    mail body: 'Integration testing Successful',
                    subject: 'Build Status',
                    to: 'kavinduisiwara@gmail.com',
                }
                failure {
                    mail body: 'Integration Tests Stage Failed',
                    subject: 'Build Status',
                    to: 'kavinduisiwara@gmail.com',
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Running code analysis using SonarQube...'
                // Integrate SonarQube for code analysis
                // Tool: SonarQube
            }
        }
       
        stage('Security Scan') {
            steps {
                echo 'Performing security scan using OWASP Dependency-Check...'
                // Perform a security scan on the code using OWASP Dependency-Check
                // Tool: OWASP Dependency-Check
            }
             post {
                success {
                    mail body: 'Security Scan Successful',
                    subject: 'Build Status',
                    to: 'kavinduisiwara@gmail.com',
                }
                failure {
                    mail body: 'Security Scan Stage Failed',
                    subject: 'Build Status',
                    to: 'kavinduisiwara@gmail.com',
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying the application to staging server...'
                // Deploy the application to a staging server (e.g., AWS EC2 instance)
                // Tool: AWS CLI, SSH plugin
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging environment...'
                // Run integration tests on the staging environment
                // Tool: Selenium, Cucumber, Postman
            }
           
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying the application to production server...'
                // Deploy the application to a production server (e.g., AWS EC2 instance)
                // Tool: AWS CLI, SSH plugin
            }
        }
    }
}