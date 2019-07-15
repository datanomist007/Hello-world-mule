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
   }
   stage ('Email_Notification') {
  try {
     echo "${currentBuild.currentResult}"
      currentBuild.result = 'SUCCESS'
    }
  catch (e) {
     echo "${currentBuild.currentResult}"
    currentBuild.result = 'FAILURE'
  }
  finally {
    mail to: 'haridasuvenkatesh@gmail.com',
      subject: "Status of pipeline: ${currentBuild.fullDisplayName}",
      body: "${env.BUILD_URL} has result ${currentBuild.result}"
  }
}
}
