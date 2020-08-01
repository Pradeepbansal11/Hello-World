pipeline{
    agent any
    stages{
        stage("Git checkout"){
            steps{
                git credentialsId: 'jenkins', url: 'https://github.com/Pradeepbansal11/Hello-World.git'
            }
        }
        stage("amven Build"){
            steps{
                sh "mvn clean package"
            }
        }
    }
}
