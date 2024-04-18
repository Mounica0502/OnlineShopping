pipeline {
    agent any
    tools {
        jdk 'OracleJDK8'
        maven 'maven3'
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
                withSonarQubeEnv(credentialsId: 'Sonar-token') {
                    sh 'mvn clean package sonar:sonar'
                }
            }
        }
    }
}