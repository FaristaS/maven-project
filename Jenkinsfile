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
}
}
