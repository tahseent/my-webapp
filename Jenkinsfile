pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out your Maven project from GitHub
                git 'https://github.com/tahseent/my-webapp.git'
            }
        }
        
        stage('Build') {
            steps {
                // Build your Maven project using Maven
                sh 'mvn clean package'
            }
        }
        
        stage('Deploy to Tomcat') {
            steps {
                // Deploy the WAR file to Tomcat
                sh '''
                    cp target/my-webapp.war /path/to/tomcat/webapps/
                    /path/to/tomcat/bin/shutdown.sh
                    /path/to/tomcat/bin/startup.sh
                '''
            }
        }
    }
    
    post {
        success {
            // Do something on success (e.g., send a notification)
            echo 'Deployment Successful'
        }
        failure {
            // Do something on failure (e.g., send a notification)
            echo 'Deployment Failed'
        }
    }
}
