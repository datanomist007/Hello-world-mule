node {
   stage('Checkout') { // for display purposes
      checkout scm
   }
  stage('Maven Version Check') {
        def mvnHome = tool 'M3'
        bat "${mvnHome}\\bin\\mvn -B install"
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
