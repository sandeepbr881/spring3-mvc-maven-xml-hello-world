pipeline {
agent any
    stages {
        stage('SCM') {
            steps {
                // Get some code from a GitHub repository
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
                    
                    sh "curl -v -u admin:adminadmin -T /var/lib/jenkins/workspace/spring3/target/spring3-mvc-maven-xml-hello-world-1.0-SNAPSHOT.war 'http://ec2-13-232-142-131.ap-south-1.compute.amazonaws.com:8080/manager/text/deploy?path=/jithin&update=true'"
                              
               }    
           
            
           } 
   
  
            
    }
        
    }
