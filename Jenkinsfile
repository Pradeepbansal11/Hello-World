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
                sh "mv /var/lib/jenkins/workspace/First_pipeline/webapp/target/*.war /var/lib/jenkins/workspace/First_pipeline/webapp/target/webapp.war"
            }
        }
    }
}
