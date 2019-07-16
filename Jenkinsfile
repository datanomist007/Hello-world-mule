node {
   def jdkHome
   def mvnHome
   stage('Checkout') { // for display purposes
      checkout scm
   }
   stage('Code Quality Check') {
      jdkHome = tool 'jdk'
      mvnHome = tool 'maven'
   ArtifactName = readMavenPom().getArtifactId()
   Version = readMavenPom().getVersion()
      echo "Code quality analysis : ${mvnHome}"
   }
   stage('Build') {
      echo 'Build is completed successfully'
      echo "artifactId : ${ArtifactName}"
      echo "Version : ${Version}"
        sh 'mvn -v'
      sh 'mvn clean'
    }
   stage('Munit') {
      echo 'Munit test cases'
      echo "Build ${BUILD_NUMBER} : ${BUILD_URL}"
      emailext body: "${BUILD_URL} has result ${currentBuild.currentResult}", subject: "Status of pipeline: ${currentBuild.fullDisplayName}", to: 'praveenbodasingi@gmail.com'
   }
}
