pipeline {
    agent any
    tools {
           jdk "java-1.8"
           maven "Maven-3.3.9"
    }
    triggers {
        pollSCM '* * * * *'
    }
    stages {
            stage ('Checkout') {
             checkout scm
        } 
        stage ('build') {
            sh 'mvn clean install'
        }
    }  
}
