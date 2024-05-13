pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Stage 1: Build - Compiles source code and packages it into an executable or distributable format.'
                echo 'Tool used: Maven - a build automation tool used primarily for Java projects.'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Stage 2: Unit and Integration Tests - Runs automated tests to verify the functionality of individual units of code and their interaction.'
                echo 'Tool is used: JUnit for unit testing and Selenium for integration testing.'
            }
            post {
                success {
                    emailext attachLog: true, body: 'Please find the attached console output.', subject: 'Pipeline Execution Report', to: 'kavinduisiwara@gmail.com'
                }
                failure {
                    emailext attachLog: true, body: 'Please find the attached console output.', subject: 'Pipeline Execution Report', to: 'kavinduisiwara@gmail.com'
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Stage 3: Code Analysis - Analyzes the source code for potential bugs and anti-patterns to ensure quality and maintainability.'
                echo 'Tool used: SonarQube - provides continuous inspection of code quality.'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Stage 4: Security Scan - Scans the code, dependencies, and configurations for known security vulnerabilities.'
                echo 'Tool is used: OWASP Dependency Check - identifies project dependencies and checks if there are any known, publicly disclosed vulnerabilities.'
            }
            post {
                always {
                    emailext attachLog: true, body: 'Security scan done, Please find the attached console output.', subject: 'Pipeline Execution Report', to: 'kavinduisiwara@gmail.com'
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Stage 5: Deploy to Staging - Deploys the application to a staging environment where it can be tested in a production-similar setup.'
                echo 'Tool used: Jenkins SSH Plugin - allows the automation of commands over SSH, useful for deployment.'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Stage 6: Integration Tests on Staging - Runs integration tests in the staging environment to validate the application against the production-like setup.'
                echo 'Tool being used: Postman (for API testing) or Selenium (for UI testing).'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Stage 7: Deploy to Production - Deploys the application to the production environment where it becomes accessible to end-users.'
                echo 'Tool used: Jenkins SSH Plugin - used for executing remote commands necessary for deploying applications.'
            }
        }
    }

    post {
        always {
            echo 'General notification: The pipeline has completed execution.'
            // Archive console output
            archiveArtifacts artifacts: '**/console.log', allowEmptyArchive: true

            // Send email with console output as attachment
            emailext (
                to: 'kavinduisiwara@gmail.com',
                subject: 'Pipeline Execution Report',
                body: 'Please find the attached console output.',
                attachmentsPattern: '**/console.log'
            )
        }
    }
}