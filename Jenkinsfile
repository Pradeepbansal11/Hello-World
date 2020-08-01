pipeline{
    agent any
    stages{
        stage("Welcome Kit"){
            steps{
                echo "Welcome to the Jenkins world"
            }
        }
        stage{
            steps("Git Welcome Kit"){
              git credentialsId: 'jenkins', url: 'https://github.com/Pradeepbansal11/Hello-World.git'
            }
        }
    }
}
