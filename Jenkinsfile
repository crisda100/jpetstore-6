pipeline {
    agent any
    
    tools{
        jdk 'jdk11'
        maven 'maven3'
    }

    environment {
        SCANNER_HOME = tool 'sonar-scanner'
    }

    stages {
        stage('Checkout repo') {
            steps {
                git changelog: false, poll: false, url: 'https://github.com/crisda100/jpetstore-6.git'
                
            }
        }
        stage('Compile') {
            steps {
                sh 'mvn clean compile'
            }
        }
      stage('SonarQube analysis') {
            steps {
                sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.url=http://144.22.35.11:9000/ -Dsonar.login=squ_456ef43eca1d43f987b49bf5325fb584919b0cf1 \
                       -Dsonar.projectName=petstore -Dsonar.java.binaries=. \
                       -Dsonar.projectKey=petstore '''
            }
        } 

        stage('OWASP Dependency Check') {
          steps {
        dependencyCheck additionalArguments: ' --scan ./', odcInstallation: 'DP'
            dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
            }
        }
    }
}

