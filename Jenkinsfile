node {
   def mvnHome
   stage('Checkout') { // for display purposes
      checkout scm
   }
   stage('Code Quality Check') {
      mvnHome = tool 'Maven-windows'
      bat(/"${mvnHome}\bin\mvn" clean package /)
      echo 'Code quality analysis'
   }
   stage('Build') {
      echo 'Build is completed successfully'
   }
   stage('Munit') {
      echo 'Munit test cases'
   }
}
