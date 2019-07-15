node {
   def jdkHome
   def mvnHome
   stage('Checkout') { // for display purposes
      checkout scm
   }
   stage('Code Quality Check') {
      jdkHome = tool 'jdk'
      mvnHome = tool 'maven'
      stages {
    stage("Build") {
      steps {
        sh 'mvn -v'
      }
    }
      echo 'Code quality analysis : $mvnHome'
   }
   stage('Build') {
      echo 'Build is completed successfully'
   }
   stage('Munit') {
      echo 'Munit test cases'
   }
}
