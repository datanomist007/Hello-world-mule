node {
   stage('Checkout') { // for display purposes
      checkout scm
   }
   stage('Build') {
      sh 'mvn clean install'
   }
}
