pipeline {
    agent any

    stages {
        stage('SCM Checkout') {
            git 'https://github.com/prakashk0301/maven-project'
        }
    } {
        stage('Compile Stage') {
            steps {
                withMaven(maven: 'maven-project') {
                    sh 'mvn clean compile'
                }
            }
        }
    } {
        stage('Test') {
            steps {
                withMaven(maven: 'maven-project') {
                    sh 'mvn clean test'
                }
            }
        }
    } {
        stage('ins') {
            steps {
                withMaven(maven: 'maven-project') {
                    sh 'mvn clean install'
                }
            }
        }
    }

  
