@Library('my-shared-library') _

pipeline{

    agent any

    parameters{

        choice(name: 'action', choices: 'create\ndelete', description: 'Choose create/Destroy')
    }

    stages{

        when { expression { param.action == 'create'}}
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
        when { expression { param.action == 'create' }}
            steps{
                script{
                    mvnTest()
                }

            }
        }
        stage('integration test maven'){
        when { expression { param.action == 'create' }}
            steps{
                script{
                    mvnIntegrationTest()
                }
            } 
        }
    }
}