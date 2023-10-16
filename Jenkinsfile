pipeline {
    agent any
    tools{
        maven "maven"
    }

    stages{
        stage('Checkout')
        {
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/tahseent/my-webapp.git']])            
   
            }
        }
        stage('Build')
        {
            steps{
                sh 'mvn clean install'
            }
        }
        stage('Deploy')
        {
            steps{
                deploy adapters: [tomcat9(credentialsId: '374837a6-ae18-40da-86d2-5c87428223e3', path: '', url: 'http://localhost:8080/')], contextPath: null, war: '**/*.war'
            }
        }
    }
    }
