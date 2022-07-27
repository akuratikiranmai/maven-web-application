node
{
     def mavenHome =tool name: "maven3.6.3" ,type: "maven"
        stage('CodeCheckout'){
       git branch: 'development', credentialsId: 'git-credentials', url: 'https://github.com/akuratikiranmai/maven-web-application.git' 
    }
    
    stage('Build'){
    sh "${mavenHome}/bin/mvn clean package"
        
    }
    stage('Sonarqube'){
        sh "${mavenHome}/bin/mvn sonar:sonar"
    }
    stage('UploadAtrifact'){
        
     sh "${mavenHome}/bin/mvn deploy"
    }
  /*  stage('DeployAppIntoTomcat'){
    sshagent(['bca50d09-3aaa-4571-91a5-5ec4453c8ab2']) {
        
        
         sh "scp -o target/maven-web-application.war ec2-user@52.70.155.144:/opt/apache-tomcat-9.0.65/webapps/"
    }
    }*/
    
}

