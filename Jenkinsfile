node {
   stage('Checkout') { // for display purposes
      checkout scm
   }
   tools {
   maven 'apache-maven-3.0.1'
   java 'java-1.8.0_181-b13'
   }
   stage('Code Quality Check') {
      echo 'Code quality analysis'
   }
   stage('Build') {
      echo 'Build is completed successfully'
   }
   stage('Munit') {
      echo 'Munit test cases'
   }
}
