node {
   def jdkHome
   def mvnHome
   stage('Checkout') { // for display purposes
      checkout scm
   }
   stage('Code Quality Check') {
      jdkHome = tool 'jdk'
      mvnHome = tool 'maven'
      echo 'Code quality analysis : $mvnHome'
      sh 'mvn clean'
   }
   stage('Build') {
      echo 'Build is completed successfully'
      sh 'mvn package'
   }
   stage('Munit') {
      echo 'Munit test cases'
   }
}
