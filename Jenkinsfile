pipeline{
    agent any
    stages{
        stage('git check out'){
            steps{
                script{
                    git branch: 'main', url: 'https://github.com/SamipDave/jenkins_project.git'
                }
            }
        }
    }
}
