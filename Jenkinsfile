node
{
stage ('SCM Checkout'){
git 'https://github.com/basmasherif/Repo1'
} 
stage('Compile-Package'){
  //get mvn Home path
def mvnHome = tool name: 'M3', type: 'maven'
  sh "${mvnHome}/bin/mvn package"
}
stage('Build Docker Image'){
sh 'docker build -t basmasherif/dockerapp:1.0.0  .'

stage('Push Docker Image'){
withCredentials([string(credentialsId: 'docker-pass', variable: 'dockerHubPwd'), string(credentialsId: 'docker-pass', variable: '')]) {
 sh "docker login -u basmasherif -p ${dockerHubPwd}"
}
sh 'docker push basmasherif/dockerapp:1.0.0 '
}
stage('Run container on Dev Server'){
  def DockerRUN = 'docker run -p 8080:8080 -name dockerapp -d basmasherif/dockerapp:1.0.0'
  sshagent(['dev-server']) {
    sh 'ssh -o StrictHostKeyChecking=no username@IP ${DockerRUN}'
}

}
  
}
