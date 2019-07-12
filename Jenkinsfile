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
      sh 'mvn package'
   }
   stage('Build') {
      echo 'Build is completed successfully'
   }
   stage('Munit') {
      echo 'Munit test cases'
   }
}
