pipeline {
    agent any
    
    tools{
        jdk 'jdk11'
        maven 'maven3'
    }

    stages {
        stage('Checkout repo') {
            steps {
                git changelog: false, poll: false, url: 'https://github.com/crisda100/jpetstore-6.git'
                
            }
        stage('Compile') {
            steps {
                sh 'mvn clean compile '
            }
        stage('Compile') {
            steps {
                sh 'mvn clean compile '
            }
        
            post {
                success {
                 echo 'Job executed success'
                }
            }
        }
    }
}
