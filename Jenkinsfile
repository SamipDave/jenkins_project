@Library('my-shared-library') _

pipeline{
    agent any

    parameters{
        choice(name: 'action', choices: 'create\ndelete', description: 'Choose Create/Destroy')
    }
    stages{

        stage('git check out'){

        when { expression {param.action == 'create' }}
        }
            steps{
                    gitCheckOut(
                        branch: "main",
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
