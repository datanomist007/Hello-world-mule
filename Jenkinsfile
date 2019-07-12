node {
   def mvnHome
   stage('Checkout') { // for display purposes
      checkout scm
   }
   stage('Code Quality Check') {
      mvnHome = tool 'Maven-linux'
      echo 'Code quality analysis : $mvnHome'
   }
   stage('Build') {
      echo 'Build is completed successfully'
   }
   stage('Munit') {
      echo 'Munit test cases'
   }
}
