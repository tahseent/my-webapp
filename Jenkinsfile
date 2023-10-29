node{
    def tomcatWeb = 'C:\\Program Files\\Apache Software Foundation\\Tomcat 9.0\\webapps'
    def tomcatBin = 'C:\\Program Files\\Apache Software Foundation\\Tomcat 9.0\\bin'
    def tomcatStatus = ''
    stage('SCM Checkout')
    {
        git 'https://github.com/tahseent/my-webapp.git'
    }
    stage('create war file')
    {
        def mvnHome = tool name: 'maven' , type: 'maven'
        bat "${mvnHome}/bin/mvn package"
    }
    stage('Deploy')
    {
        bat "copy target\\my-webapp.war \"${tomcatWeb}\\my-webapp.war\""
    }
}
