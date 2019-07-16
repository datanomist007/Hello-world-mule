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
      try{
      if(isMasterBranch()){
      sh 'mvn clean install'
      }
         else{
         isDevelopeBranch()}
        currentBuild.currentResult = 'SUCCESS' 
      notifySuccessful()
    }
      catch(e){
      currentBuild.currentResult = 'FAILURE'
                echo "ERROR: ${e}"
            } finally {
               notifyFailed() 
            }
   }
   stage('Munit') {
      echo 'Munit test cases'
      echo "Build ${BUILD_NUMBER} : ${BUILD_URL}"
   }
   }
def notifyFailed() {
   emailext (
      to: 'haridasuvenkatesh@gmail.com',
      subject: "Status of pipeline: ${currentBuild.fullDisplayName}",
      body: "${BUILD_URL} has result ${currentBuild.currentResult}"
     )
 }
   def notifySuccessful() {
   emailext (
       to: 'haridasuvenkatesh@gmail.com',
      subject: "Status of pipeline: ${currentBuild.fullDisplayName}",
      body: "${BUILD_URL} has result ${currentBuild.currentResult}"
     )
 }
def isMasterBranch() {
    return this.config.branchName == 'master'
}

def isDevelopBranch() {
    return this.config.branchName == 'developement'
}
