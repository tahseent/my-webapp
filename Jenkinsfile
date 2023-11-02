pipeline{
    agent any
    tool{
        maven "maven"
    }
    stages
    {
        stage("Checkout"){
        step{
            git ''
        }
        }
        stage("Build"){
        step{
            sh 'mvn clean install'
    }
    }
        stage("Deploy")
        {
            step{
                deploy adapters: [tomcat9(credentialsId: 'tomcat_id', path: '', url: 'http://localhost:7080/manager/html')], contextPath: 'sample', war: '**/*.war'
            }
}
}
