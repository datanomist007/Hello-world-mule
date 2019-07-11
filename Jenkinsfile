node {
   stage('Checkout') { // for display purposes
      checkout scm
   }
   tools {
   maven 'apache-maven-3.0.1'
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
