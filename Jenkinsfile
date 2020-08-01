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
                sh 'mvn clean package'
                sh 'mv /var/lib/jenkins/workspace/First_pipeline/webapp/target /var/lib/jenkins/workspace/First_pipeline/webapp/target/webapp.war
            }
        }
        stage("Deploy_build"){
            sshagent(['tomcat-dev']) {
                sh """
                scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/First_pipeline/webapp/target/webapp.war ec2-user@100.25.183.59:/opt
                
                ssh ec2-user@100.25.183.59/root/tomcat8/bin/shutdown.sh
                
                ssh ec2-user@100.25.183.59/root/tomcat8/bin/startup.sh
                
                """
           }
        }
    }
}
