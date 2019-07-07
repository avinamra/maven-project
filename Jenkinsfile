pipeline {
    agent any

    stages {
        stage('SCM Checkout') {
            git 'https://github.com/prakashk0301/maven-project'
        }
    } {
        stage('Compile Stage') {
            agent { label 'maven'}
            steps {
                withMaven(maven: 'maven-project') {
                    sh 'mvn clean compile'
                }
            }
        }
    }
        stage('Test') {
            steps {
                withMaven(maven: 'maven-project') {
                    sh 'mvn clean test'
                }
            }
        }
    
        stage('ins') {
            steps {
                withMaven(maven: 'maven-project') {
                    sh 'mvn clean install'
                }
            }
        }
    
        stage('deploying'){
            steps {
               sshagent (credentials: ['9ab64fbb-f839-471c-bd1f-e190e39a4b55']) {
                  sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.80.82:/var/lib/tomcat/webapps'
    }
    }
}
}

