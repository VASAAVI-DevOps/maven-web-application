node{
    
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])
    
    def mavenHome = tool name: "Maven 3.8.3"
stage('CheckoutCode'){
git branch: 'development', credentialsId: 'eb612bea-115b-4238-8c69-47ab63cb20ab', url: 'https://github.com/VASAAVI-DevOps/maven-web-application.git'
}

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}
/*
stage('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn sonar:sonar"
}
stage('UploadArtifactIntoNexusRepo'){
sh "${mavenHome}/bin/mvn deploy"
}

stage('DeployApplicationintoTomcatServer')
{
sshagent(['d6f6a414-b9e6-437f-aa80-642ffa36c02c']) {
  sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.110.42.131:/opt/apache-tomcat-9.0.58/webapps/"
}

}
*/
}
