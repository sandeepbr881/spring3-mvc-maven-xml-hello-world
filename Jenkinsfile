pipeline {
agent any
      
      tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "maven3"
    }

   stages {
        stage ('SCM') {
            steps {
                 git credentialsId: 'github_credentials1', url: 'https://github.com/Ratheesh1986/spring3-mvc-maven-xml-hello-world.git'
                }
           }
        stage ('Build') {
            steps {
                 sh "mvn -Dmaven.test.failure.ignore=true clean package"
                }
           }
           
        stage ('artifacts') {
            steps {
                
                 archiveArtifacts 'target/*.war'
                }
           }
         
         stage('deploy') {
            steps {
                // Tomcat deploy
                
                withCredentials([usernameColonPassword(credentialsId: 'tomcat_credential', variable: 'tomcatusa')]) {sh "curl -v -u ${tomcatusa} -T /var/lib/jenkins/workspace/spring3/target/spring3-mvc-maven-xml-hello-world-1.0-SNAPSHOT.war 'http://ec2-15-207-54-130.ap-south-1.compute.amazonaws.com:8080/manager/text/deploy?path=/spring100&update=true'"
    
                   }
                    
                    
               } 
         
           
       }   
           
    }   
           
}       
