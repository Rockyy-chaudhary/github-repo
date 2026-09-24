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
        stage('this stage is for code quality check by sonarcloud'){
            steps {
                script {
                    def sonar_home = tool 'SONARCLOUD'
                    withSonarQubeEnv('SonarQube') {
                            echo "after succesful build we run tsonar-scanner \
                            sh " " "
                            ${sonar_home}/bin/sonar-scanner
                            -Dsonar.organization=sonartestorg0111 \
                            -Dsonar.projectKey=sonartestorg0111_sonartesthe cose quality by sonarqube/cloud see output is in sonarcloud dashboard"
                            -Dsonar.sources=src/main/java \
                            -Dsonar.coverage.exclusions=**/*.java \
                            -Dsonar.coverage.newCode.requiredCoverage=0 \
                            -Dsonar.newCode.period=1 \
                            -Dsonar.qualitygate.wait=true \
                            -Dsonar.host.url=https://sonarcloud.io          
                            """
                    }
                }
                    
        }
        }
    }
    post {
        always { 
            echo 'Pipeline finished.' 
        }
        success { 
                echo 'pull from github,build and sonar scanner completed!' 
        } 
        failure { 
            echo 'pipeline failed check the logs' 
        } 
        unstable { 
            echo 'Build is unstable.' 
        } 
        aborted { 
            echo 'pull from github was aborted.' 
        }

    }
}

