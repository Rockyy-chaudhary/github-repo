pipeline {
    agent {
        label 'BUILD'
    }

    stages{
        stage('Git checkout') {
            steps{
                echo"jenkins pull code from your github repo"
                git(branch: "master" ,credentialsId: "GITHUB" ,url: "https://github.com/Rockyy-chaudhary/github-repo.git")
            }
        }
        stage( 'post result') {
            always { 
                echo 'Pipeline finished.' 
                }
                 success { 
                    echo 'pull from github succeeded!' 
                } 
                failure { 
                    echo 'pull from github failed!' 
                } 
                unstable { 
                    echo 'Build is unstable.' 
                } 
                aborted { 
                    echo 'pull from github was aborted.' 
                }

            }
        }
    }
}