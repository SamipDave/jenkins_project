@Library('my-shared-library') _

pipeline{
    agent any
    stages{
        stage('git check out'){
            steps{
                    gitCheckOut(
                        branch: "mian",
                        url: "https://github.com/SamipDave/jenkins_project.git"
                 )
            }
        }
        stage('unit test mvn'){
            steps{
                script{
                    mvnTest()
                }
            }

        }
    }
}
