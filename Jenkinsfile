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
      sh 'mvn clean install'
    }
   stage('Munit') {
      echo 'Munit test cases'
      echo "Build ${BUILD_NUMBER : ${BUILD_URL}"
   }
   post {
        failure {
            // notify users when the Pipeline fails
            mail to: 'haridasuvenkatesh@gmail.com',
               subject: "Failed Pipeline ${env.BUILD_NUMBER}: ${currentBuild.fullDisplayName}",
                    body: "Something is wrong with ${env.BUILD_URL}"
        }
    }
}
