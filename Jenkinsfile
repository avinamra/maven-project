pipeline {
    agent any


    stages 
    {  
        
        stage ('SCM Checkout') {
          git 'https://github.com/avinamra/maven-project'
         }
    
    }
    {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'maven-project') 
                {   
                    sh 'mvn compile' 
                }
                }
                  }
                                
            
        
        
        stage ('Testing Stage') {


            steps {
                withMaven(maven : 'maven-project')
                {
                    sh 'mvn test'
                }
                  }
                                 
        }

        
        stage ('install Stage') {
            steps {
                withMaven(maven : 'maven-project')
                {
                    sh 'mvn install'
                }
                                  
                   }
        }

        stage ('deploy to tomcat') {
           steps {
               sshagent(['6602e53d-1bf6-4da0-b105-8b9697292eb5']) {
                  sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.39.35:/var/lib/tomcat/webapps'
    }      
}
        }
    }
}
