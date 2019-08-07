pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git 'https://github.com/prakashk0301/maven-project'
        }
  }
    {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'maven') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'maven') {
                    sh 'mvn test'
                }
            }
        }


        stage ('install Stage') {
            steps {
                withMaven(maven : 'maven') {
                    sh 'mvn install'
                    }
            }
        }
                    
        stage ('deploy to tomcat') {
            steps {
                sshagent(['ssh-key']) {
                    sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.43.64:/var/lib/tomcat/webapps'
                }
            }
        }

         
}
}
