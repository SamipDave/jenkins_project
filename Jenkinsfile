@Library('my-shared-library') _

pipeline{
    agent any
    stages{
        stage('git check out'){
            steps{
                    gitCheckOut(
                        branch: "main",
                        url: "https://github.com/SamipDave/jenkins_project.git"
                    )
            }
        }
    }
}
