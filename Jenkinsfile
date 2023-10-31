pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout source code from your version control system (e.g., Git)
                git 'https://github.com/tahseent/my-webapp.git'
            }
        }

        stage('Build') {
            steps {
                // Perform any build steps, such as compiling, packaging, etc.
                sh 'mvn clean package' // Example for a Maven-based project
            }
        }

        stage('Test') {
            steps {
                // Run tests here
                sh 'mvn test' // Example for running tests using Maven
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                // Deploy the application to Tomcat
                sh '''
                    cp target/my-webapp.war C://Program Files//pache Software Foundation//Tomcat 9.0//webapps
                    # Restart Tomcat to apply changes
                    C://Program Files//pache Software Foundation//Tomcat 9.0/bin/shutdown.sh
                    C://Program Files//pache Software Foundation//Tomcat 9.0/bin/startup.sh
                '''
            }
        }
    }
}
