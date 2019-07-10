pipeline {
    agent any
    
    tools {
           jdk "java-1.8"
           maven "Maven-3.3.9"
    }
    
    stages {
        stage ('Initialize') {
            steps {
                sh
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
            }
        }
        stage('Checkout'){
             checkout scm
        } 
        stage('build'){
            sh 'mvn clean install'
        }
    }  
}
