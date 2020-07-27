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
        stage("Maven Package"){
            steps{
                sh "mvn clean package"
                sh "mv target/*.war target/myweb.war"
            }
        }
        steps{
            sshagent(['tomcat']) {
        sh """
            scp -o StrictHostKeyChecking=no target/myweb.war ec2-uer@172.31.50.36:/opt/tomcat8/webapps/
            
            ssh ec2-uer@172.31.50.36:/opt/tomcat8/bin/shutdown.sh
            ssh ec2-uer@172.31.50.36:/opt/tomcat8/bin/startup.sh
        
        """
        }
      }
    }
}
