 pipeline {
      agent any
      stages {
        stage ('clone git code'){
          git 'https://github.com/avinamra/maven-project'
          }
        stage ('compile my code'){
        
          steps {
             withMaven(maven : 'localMaven'){
               sh 'mvn compile'
               }
               }
               }
               }
