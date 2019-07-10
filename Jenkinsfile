pipeline {
    agent any

    tools {
        maven 'maven' 
    }

    stages {
        stage('Checkout') {
            checkout scm
        }
        stage('FEATURE Build and Test') {
            when {
                allOf {
                    branch 'feature-*' 
                }
            } 
            steps { 
                sh 'mvn -s settings.xml clean test' 
            }
        }
        
        stage('DEV and TEST Build, Test, and Deploy') {
            when {
                expression {
                    return params.IS_RELEASE == false
                }
                branch 'dev-*'
            } 
            steps { 
                sh 'mvn -s settings.xml clean deploy'
            }
        }
        
        stage('Prepare Release') {
            when {
                expression {
                    return params.IS_RELEASE
                }
                branch 'dev-*'
            } 
            steps {
                script {
                    def lastCommit = sh returnStdout: true, script: 'git log -1 --pretty=%B'
                    if (lastCommit.contains("[maven-release-plugin]")){
                        sh "echo  Commit done by Maven Release Plugin - build is being skipped"

                    } else {
                    //checkout needs to be done, because Jenkins uses shallow clones, which causes 
                    //“Git fatal: ref HEAD is not a symbolic ref” exception while using Maven Release Plugin
                        sh "git checkout ${env.BRANCH_NAME}"
                        sh 'mvn -s settings.xml clean release:prepare'
                        sh 'mvn -s settings.xml release:perform' 
                    }
                } 
            }
        }
        
        stage('PROD Build and Test') {
            when {
                allOf {
                    branch 'master' 
                }
            } 
            steps { 
                sh 'mvn -s settings.xml clean test' 
            }
        }
        
    }

    post {
        always {
            archive 'target/**/*.zip'
            archive 'target/munit-reports/coverage-json/**/*.json'
            junit 'target/surefire-reports/**/*.xml'
            cleanWs()
        }
    }
}
