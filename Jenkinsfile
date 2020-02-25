node
{
stage (‘SCM Checkout’){
git ‘https://github.com/basmasherif/Repo1‘
} 
stage(‘Compile-Package’){
  //get mvn Home path
def mvnHome = tool name: 'M3', type: 'maven'
  sh "${mvnHome}/bin/mvn package"
}
}
