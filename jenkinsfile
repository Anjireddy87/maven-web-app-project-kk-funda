node //by default build-in master node
{
   def mavenHome=tool name: "Maven3.9.9"
   stage('git checkout')
   {
   git branch: 'development', credentialsId: 'fd50f360-76ba-4e00-a2d2-b23fa399de02', url: 'https://github.com/Anjireddy87/maven-web-app-project-kk-funda.git'
   }
   stage('Build-Code')
   {
   sh "${mavenHome}/bin/mvn clean package"
   }
   stage('Qualitycheck')
   {
   sh "${mavenHome}/bin/mvn clean sonar:sonar"
   }
   stage('StoreArtifactorytoRemote')
   {
    sh "${mavenHome}/bin/mvn clean deploy"
   }
   
   stage('DeploytoAppserver')
   {
    sh """
           curl -u Anjireddy:Anji@Nani@123 \
           --upload-file /var/lib/jenkins/workspace/jio-scripted-way-pipepline-development/target/maven-web-application.war \
           "http://3.95.225.220:8080/manager/text/deploy?path=/maven-web-application&update=true"
       """
   }
      
}// node closing 
