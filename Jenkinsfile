pipeline{
    agent any
    stages{
        stage('git check out'){
            steps{
                script{
                    gitCheckOut(
                        branch: "mian",
                        url: "https://github.com/SamipDave/jenkins_project.git"
                    )
                }
            }
        }
    }
}
