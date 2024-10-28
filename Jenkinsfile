@Library('my-shared-library') _

pipeline{

    agent any

    parameters{

        choice(name: 'action', choices: 'create\ndelete', description: 'Choose create/Destroy')
        string(name: 'ImageName', description: "name of the docker build", defaultValue: 'javaapp')
        string(name: 'ImageTag', description:  "tag of the docker build", defaultValue: 'v1')
        string(name: 'DockerHubUser', description: "name of the Application", defaultValue: 'samipdave')
    }

    stages{

        
        stage('Git Checkout'){
            when { expression { params.action == 'create' }}
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
            when { expression { params.action == 'create' }}
            steps{
                script{
                    mvnTest()
                }

            }
        }
        stage('integration test maven'){
            when { expression { params.action == 'create' }}
            steps{
                script{
                    mvnIntegrationTest()
                }
            } 
        }
        stage('static code analysis: Sonarqube'){
            when { expression { params.action == 'create' }}
                steps{
                    script{
                        def SonarQubecredentialsId = 'sonarqube-api'
                        staticCodeAnalysis (SonarQubecredentialsId)
                }
            }
        }
        stage('quality Gate status check : sonarqube'){
            when { expression { params.action == 'create' }}
                steps{
                    script{
                        def SonarqubecredentialsId = 'sonarqube-api'
                        qualityGate(SonarqubecredentialsId)
                }
            }
        }
        stage('Maven Build : maven'){
            when { expression { params.action == 'create' }}
                steps{
                    script{

                        mvnBuild()
                }
            }
       }
       stage('Docker Image Build'){
            when { expression { params.action == 'create' }}
                steps{
                    script{

                        dockerbuild("${params.ImageName}","${params.ImageTag}","${params.DockerHubUser}")

                }
            }
       }
    }
}