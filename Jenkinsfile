pipeline{
    agent any
    stages{
        stage("Git Checkout"){
            steps{
                git credentialsId:'tahseent', url: 'https://github.com/tahseent/my-webapp.git'
            }
        }
        stage("Maven Build"){
            steps{
                sh "mvn clean package"
                sh "mv target/*.war target/my-webapp.war"
            }
        }
        stage("Tomcat Deploy"){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcat-user', path: '', url: 'http://localhost:8080/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
