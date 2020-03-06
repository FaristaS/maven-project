pipeline {
agent any
stages {
stage('SCM Checkout'){
git 'https://github.com/FaristaS/maven-project'
}
}
{
stage ('Compile Stage') {
agent { label 'maven' }
steps {
withMaven(maven : 'MVN-3.5') {
sh 'mvn clean compile'
}
}
}

stage ('Test Stage') {
steps {
withMaven(maven : 'MVN-3.5') {
sh 'mvn test'
}
}
}
  
stage ('Install Stage') {
steps {
withMaven(maven : 'MVN-3.5') {
sh 'mvn clean install'
}
}
}

stage ('Deploy Stage') {
steps {
sshagent (credentials: ['797299e4-e512-4fd7-8fd7-210477e058f5']) {
sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@20.0.10.122:/var/lib/tomcat/webapps'
}
}
}  

  
}
}
