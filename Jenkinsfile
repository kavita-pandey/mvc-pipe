pipeline {
    agent any

    triggers {
        pollSCM '* * * * *'
    }

    environment{
            mvnHome=tool name: 'Maven', type: 'maven'
            mvnCmd = "${mvnHome}/bin/mvn"
        }

    stages {
        stage('Build') {
            steps{
                // Get source code from a GitLab repository
                git 'https://git.nagarro.com/GITG00641/Java/abhinav-amar/tree/master/SpringRest_Devops'
                bat "${mvnCmd} clean package"
            }
        }
        stage('Running') {
            steps{
                bat "taskkill /F /PID 8852"
                bat "${mvnCmd} spring-boot:run"
            }
        }
    }
}