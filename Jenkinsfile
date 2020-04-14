node{
stage('SCM checkout')
{
  git 'https://github.com/Rameshrs777/Newjenkins'
}
stage('Compile-Package')
{
  //Get maven Home path
  def mvnHome = tool name: 'maven', type: 'maven'
  sh "${mvnHome}/bin/mvn package"
}
}
