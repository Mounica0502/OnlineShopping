pipeline {
    agent any
    tools {
        jdk 'OracleJDK8'
        maven 'maven3'
    }
    environment {
             SCANNER_HOME=tool'sonar-scanner'
          }

    stages {
        stage('Git checkout') {
            steps {
                git branch: 'ci-jenkins', url: 'https://github.com/Mounica0502/Onlineshopping.git'
            }
        }
        stage('UNIT Testing') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Integration Testing') {
            steps {
                sh 'mvn verify -DskipUnitTests'
            }
        }
        stage('Maven Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Static code analysis') {
            steps {
                    withSonarQubeEnv('Sonar-server') {    
                        sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=Onlineshopping \
                         -Dsonar.projectKey=Onlineshopping'''
                               
                  }
                }
                
            }
        
    }
}