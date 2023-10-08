pipeline
{
	agent any
	tools{
		    maven 'maven'
        }
	stages 
    {
		stage('Checkout') {
            steps {
                // Check out your Maven project from GitHub
                git 'https://github.com/tahseent/my-webapp.git'
            }
        }
		
		stage ('Build') 
        {
			steps
            {
                sh 'mvn clean package'
			}
		    post 
            {
			    success
                {
				    echo "Archiving the Artifacts"
				    archiveArtifacts artifacts: '**/target/*.war'
			    }
		    }
		}
	    stage ('Deploy to tomcat server') 
        {
		    steps
            {
		        deploy adapters: [tomcat9(path: '', url: 'http://localhost:8080/')], contextPath: null, war: '**/*.war'
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
