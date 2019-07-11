node {
   tools {
          maven 'M3'
  }
   stage('Checkout') { // for display purposes
      checkout scm
   }
  stage('Maven Version Check') {
        echo "This time, the Maven version should be 3.3.9"
        sh "mvn -version"
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
