@Library('my-shared-library') _

pipeline{

    agent any

    parameters{

        choice(name: 'action', choices: 'create\ndelete', description: 'Choose create/Destroy')
    }

    stages{

        
        stage('Git Checkout'){
            when { expression { parameters.action == 'create' }}
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
            when { expression { parameters.action == 'create' }}
            steps{
                script{
                    mvnTest()
                }

            }
        }
        stage('integration test maven'){
            when { expression { parameters.action == 'create' }}
            steps{
                script{
                    mvnIntegrationTest()
                }
            } 
        }
    }
}