node {
   def jdkHome
   def mvnHome
   ArtifactName = readMavenPom().getArtifactId()
   Version = readMavenPom().getVersion()
   stage('Checkout') { // for display purposes
      checkout scm
   }
   stage('Code Quality Check') {
      jdkHome = tool 'jdk'
      mvnHome = tool 'maven'
      echo 'Code quality analysis : ${mvnHome}'
   }
   stage('Build') {
      echo 'Build is completed successfully'
      echo 'artifactId : ${ArtifactName}'
      echo 'Version : ${Version}'
        sh 'mvn -v'
      sh 'mvn clean'
    }
   stage('Munit') {
      echo 'Munit test cases'
   }
}
