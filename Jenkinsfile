node('nodes')
{
def mavenhome = tool name: "maven 3.9.2"
stage('checkout code'){
git credentialsId: '062fe765-1723-4559-a0a8-4a6629d930ae', url: 'https://github.com/shivanandatendulkar123/time-tracker.git'
}
stage('build'){
sh "${mavenhome}/bin/mvn clean package"
}
/*
stage('sonarqube stage'){
sh "${mavenhome}/bin/mvn clean sonar:sonar"
}
stage('upload nexus repo'){
sh "${mavenhome}/bin/mvn clean deploy"
}
*/
stage ('deploy the app in tomcat server'){
sshagent(['80de34f0-4ba4-44aa-8293-da7b0219a2e2']) {
    sh "scp -o StrictHostKeyChecking=no web/target/time-tracker-web-0.5.0-SNAPSHOT.war ubuntu@3.142.50.8:/opt/apache-tomcat-9.0.75/webapps/"
}
}
/*
stage ('send email notification'){
mail bcc: 'shivanandatendulkar457@gmail.com', body: '''Build over

Regards,
shivananda tendulkar
Support mrf


''', cc: 'shivanandatendulkar457@gmail.com', from: '', replyTo: '', subject: 'build over', to: 'shivanandatendulkar457@gmail.com'
}*/
} 
