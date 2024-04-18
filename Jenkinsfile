pipeline {

    agent any
    tools{
        java 'jdk17'
        maven 'maven3'
    }



stages {

    stage('Git Checkout'){

        steps{
        git branch: 'ci-jenkins', url: 'https://github.com/Mounica0502/Onlineshopping.git'
        }
    }
    stage('UNIT Testing'){

        steps{
        sh 'mvn test'
        }
    }
}
}