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

    }      
}
