pipeline {
 agent any
 tools {
 maven 'Maven'
 }
 stages {
 stage('Build') {
 steps {
 script {
 bat "mvn clean package"
 }
 }
 post {
 success {
 echo "Archiving the Artifacts"
 archiveArtifacts artifacts: '**/target/*.war'
 }
 }
 }
 stage('Deploy to Tomcat') {
 steps {
 script {
deploy adapters: [tomcat9(credentialsId: '154ac4a3-e5aa-4b0d-a6ae-8385edbc56a1', path: '', url: 'http://localhost:8080')], contextPath: '/CI-CD-JK', war: '**/*.war'}
 }
 }
 }
}
