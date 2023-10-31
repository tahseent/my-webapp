pipeline {
    agent any
    
    environment {
        TOMCAT_URL = 'http://localhost:8080' // Update with your Tomcat URL
        TOMCAT_MANAGER_USER = 'deploy' // Update with your Tomcat Manager username
        TOMCAT_MANAGER_PASS = 'deploy' // Update with your Tomcat Manager password
    }
    
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/tahseent/my-webapp.git' // Replace with your GitHub repository URL
            }
        }
        
        stage('Build') {
            steps {
                build 'target/my-webapp.war' // Or any other Maven build commands
            }
        }
        
        stage('Deploy to Tomcat') {
            steps {
                script {
                    def warFile = sh(returnStdout: true, script: 'ls target/*.war').trim()
                    def warFileName = warFile.tokenize('/').last()
                    def curlCommand = "curl -T ${warFile} --user ${env.TOMCAT_MANAGER_USER}:${env.TOMCAT_MANAGER_PASS} ${env.TOMCAT_URL}/manager/text/deploy?path=/${warFileName}"
                    sh curlCommand
                }
            }
        }
    }
}
