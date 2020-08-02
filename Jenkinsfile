currentBuild.displayName = "FirstPipeline-#"+currentBuild.number
pipeline{
    agent any
    environment{
      PATH = "/opt/maven/bin:$PATH"
    }
    stages{
        stage("Git checkout"){
            steps{
                git credentialsId: 'jenkins', url: 'https://github.com/Pradeepbansal11/Hello-World.git'
            }
        }
        stage("maven Build"){
            steps{
                sh "mvn clean package"
                sh "mv /var/lib/jenkins/workspace/First_pipeline/webapp/target/*.war /var/lib/jenkins/workspace/First_pipeline/webapp/webapp.war"
            }
        }
        stage("Deploy-build"){
            steps{
                sshagent(['tomcat-dev']) {
                sh """
                  scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/First_pipeline/webapp/webapp.war ec2-user@172.31.61.186:/opt/webapp
                
                  #ssh ec2-user@172.31.61.186 /root/tomcat8/bin/shutdown.sh
                
                  #ssh ec2-user@172.31.61.186 /root/tomcat8/bin/startup.sh
                
                """
              }
            }
        }
    }
}
