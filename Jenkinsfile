pipeline {
    agent any
    tools {
        maven 'Maven3.6.0'
        jdk 'jdk1.8.0_121'
    }
    stages {
         stage ('Build') {
            steps {
                bat 'mvn install'
                 bat 'mvn compiler:compile'
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                }
            }
        }
        
        stage('Sonarqube analysis') {
    steps {
    script {
             scannerHome = tool 'SonarQube Scanner 2.3';
        }
     withSonarQubeEnv('SonarQube') {
       bat "${scannerHome}\\bin\\sonar-scanner.bat" 
    }

    } 
        }
        
}
    }
