pipeline{
	agent any
	tools{
		maven 'maven'
    }
	stages {
		stage ('Build') {
			steps{
					sh 'mvn clean package'
				}
		post {
			success {
				echo "Archiving the Artifacts"
				archiveArtifacts artifacts: '**/target/*.war'
			}
		}
		}
	stage ('Deploy to tomcat server') {
		steps{
      deploy adapters: [tomcat9(credentialsId: 'f3a3c68c-9a2d-4bb1-ac06-c89447379344', path: '', url: 'http://localhost:8080/')], contextPath: null, war: '**/*.war'	}
}
}
}

