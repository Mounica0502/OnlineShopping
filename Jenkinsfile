pipeline {
    agent any
    tools {
        jdk 'jdk17'
        maven 'maven3'
    }
    stages {
        stage(Git checkout) {
            steps {
                git branch: 'ci-jenkins', url: 'https://github.com/Mounica0502/Onlineshopping.git'
            }
        }
    }
}