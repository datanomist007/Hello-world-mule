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
echo 'maven  version is available'	  
   }
   stage('Build') {
      echo 'Build is completed successfully'
      echo "artifactId : ${ArtifactName}"
      echo "Version : ${Version}"
        sh 'mvn -version'
      try{
      sh 'mvn clean'
        currentBuild.result = 'SUCCESS'
    }
      catch(e){
      currentBuild.result = 'FAILURE'
                echo "ERROR: ${e}"
            } finally {
               emailNotification() 
            }
   }
   stage('Munit') {
      echo 'Munit test cases'
      echo "Build ${BUILD_NUMBER} : ${BUILD_URL}"
   }
   }
stage('Docker Build') {
      agent any
      steps {
        sh 'docker build -t venkatesh/Hello-world-mule .'
      }
    }
    stage('Docker Push') {
      agent any
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
          sh "docker login -u ${env.awsdocker789} -p ${env.aws427400}"
          sh 'docker push venkatesh/Hello-world-mule'
        }
      }
    }
def emailNotification() {
   emailext (
      to: 'haridasuvenkatesh@gmail.com',
      subject: "Status of pipeline: ${currentBuild.fullDisplayName}",
      body: "${BUILD_URL} has result ${currentBuild.currentResult}"
     )
 }
