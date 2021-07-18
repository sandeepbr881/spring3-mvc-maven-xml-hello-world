pipeline {
    agent any
          tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "maven3"
    }

    stages {
        stage('SCM') {
            steps {
                git credentialsId: 'github_credentials', url: 'https://github.com/Ratheesh1986/spring3-mvc-maven-xml-hello-world.git'
            }
        }
   
   stage('Build') {
            steps {
                // maven packages
                    sh "mvn -Dmaven.test.failure.ignore=true clean package"
                              
            }

            
       }
   
   stage ('Artifacts') {
            steps {
                
                 archiveArtifacts 'target/*.war'
                }
           }
   
   
   stage('deploy') {
            steps {
                // Tomcat deploy
                    
            

                  withCredentials([usernameColonPassword(credentialsId: 'tomcat_credential', variable: 'arunusa')]) {sh "curl -v -u ${arunusa} -T /var/lib/jenkins/workspace/spring3/target/spring3-mvc-maven-xml-hello-world-1.0-SNAPSHOT.war 'http://ec2-13-233-69-212.ap-south-1.compute.amazonaws.com:8081/manager/text/deploy?path=/Arunusa&update=true'"           
               }    
           
            
           } 
   
   
    }
}

}
