@Library('my-shared-library') _

pipeline{
    agent any

    parameters{
        choice(name: 'action', choices: 'create\ndelete', description: 'Choose Create/Destroy')
    }
    stages{
        
        when { expression { param.action == 'create' }}

        stage('git check out'){
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
}
