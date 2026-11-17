pipeline {
    agent any
    tools { jdk 'JDK21'; maven 'M3' }
    stages {
        stage('Checkout') { steps { checkout scm } }
        stage('Build') {
            steps { dir('backend') { sh 'mvn clean package -DskipTests' } }
        }
        stage('Test') {
            steps { dir('backend') { sh 'mvn test' } }
        }
        stage('Archive') {
            steps { archiveArtifacts artifacts: 'backend/target/*.jar', fingerprint: true }
        }
    }
}
