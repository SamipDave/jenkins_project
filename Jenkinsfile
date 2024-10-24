@Library('my-shared-library') _

pipeline{

    agent any

    stages{
        stage('Git Checkout'){
            steps{
                script{

                    gitCheckOut(
                        branch: "main",
                        url: "https://github.com/SamipDave/jenkins_project.git"
                    )
                }
            }
        }
        stage('unit Test maven'){
            steps{
                script{
                    mvnTest()
                }

            }
        }
    }
}