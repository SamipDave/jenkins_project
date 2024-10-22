pipeline{
    agent any
    stages{
        stage('git check out'){
            steps{
                script{
                    git branch: 'main', url: 'https://github.com/SamipDave/Jenkins_shared_library/app-main.git'
                }
            }
        }
    }
}
