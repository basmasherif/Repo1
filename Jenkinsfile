node
{
stage (‘SCM Checkout’){
def mvnHome = tool name: 'M3', type: 'maven'
git ‘https://github.com/basmasherif/Repo1.git‘
} 
stage(‘Compile-Package’){
sh ‘mvn package’
}
}
