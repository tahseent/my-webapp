pipeline
{
	agent any
	tools{
		    maven 'MVN'
        }
	stages 
    {
		
		stage ('Build') 
        {
			steps
            {
		    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: '6d59937b-1b6d-4feb-b401-43c800670887', url: 'https://github.com/tahseent/my-webapp.git']])
                sh 'mvn clean package'
			}
		    post 
            {
			    success
                {
				    echo "Archiving the Artifacts"
				    archiveArtifacts artifacts: '*/target/.war'
			    }
		    }
		}
	    stage ('Deploy to tomcat server') 
        {
		    steps
            {
deploy adapters: [tomcat9(credentialsId: '786fe9e6-086a-4455-8c2e-7b169c597430', path: '', url: 'http://localhost:8080/')], contextPath: null, war: '**/*.war'	        }
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
