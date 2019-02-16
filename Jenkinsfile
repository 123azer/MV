pipeline {
    agent any
    tools {
        maven 'Maven 3.6.0'
        jdk 'jdk1.8.0_121'
    }
    stages {
         stage ('Build') {
            steps {
                 bat 'mvn compiler:compile'
            bat 'mvn install'
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
             scannerHome = tool 'SonarScanner';
        }
     withSonarQubeEnv('SonarQube') {
       bat "${scannerHome}\\bin\\sonar-scanner.bat" 
    }

    } 
        }
        
}
    }