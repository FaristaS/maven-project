pipeline {
     agent any
     stages {
          stage('clone my SCM'){
                    git checkout 'https://github.com/FaristaS/maven-project.git'
          }
          stage('compile with maven'){
                    step {
                              withMaven(maven : 'MVN-3.5') {
                                        sh 'mvn compile'
                                        }
                           }
                           }
            }
         }
