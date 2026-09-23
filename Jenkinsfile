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
        stage('build by maven') {
            steps {
                script {
                    def maven_home = tool 'MAVEN'
                    echo"building project & running unit test (excluding test from selenium)"
                    sh "${maven_home}/bin/mvn clean verify"
                }
            }
        }
    }
    post {
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

