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
sh 'mvn install'
}
}
}

  
stage ('Deploy Stage') {
steps {
sshagent (credentials: ['797299e4-e512-4fd7-8fd7-210477e058f5']) {
sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@20.0.50.69:/var/lib/tomcat/webapps/'
}
}
}
  
}
}
