pipeline{
  agent any
  stages {
        stage('Build') {
            steps {
                echo "Build the code using Maven"
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Run unit tests using JUnit"
                echo "Run integration tests using Selenium"
            }

            post{
                success{
                    emailext(
                      subject: 'Unit and Integration Tests',
                      to: 'kavinduisiwara@gmail.com',
                      body: 'Unit and Integration Tests successfuly completed', 
                    )   
                }
                failure{
                    emailext(
                      subject: 'Unit and Integration Tests',
                      to: 'kavinduisiwara@gmail.com',
                      body: 'Unit and Integration Tests Failed. Check logs.', 
                    )   
                }
            }

        }

        
        stage('Code Analysis') {
            steps {
                echo "Integrate a code analysis tool to analyse the code using SonarQube"
            }
        }
        stage('Security Scan') {
            steps {
                echo "Perform a security scan on the code using OWASP Dependency-Check"
                }

            post{
                success{
                    emailext(
                      subject: 'Security Scan',
                      to: 'kavinduisiwara@gmail.com',
                      body: 'Security Scan Tests successfuly completed', 
                    )   
                }
                failure{
                    emailext(
                      subject: 'Security Scan',
                      to: 'kavinduisiwara@gmail.com',
                      body: 'Security Scan Tests successfuly completed', 
                    )   
                }
            }
            }
            
        stage('Deploy to Staging') {
            steps {
                echo "deploy the application to Azure Virtual Machines"
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Run integration tests on the staging environment"
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "deploy the application to a production server Azure Virtual Machines"
        }
    }
}
}
