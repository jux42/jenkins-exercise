pipeline {
    agent any

    environment {
        MESSAGE = "main message"
    }

    stages {
        stage("check") {
            steps {
                script {
                    MESSAGE = "check message"
                }
                echo "${MESSAGE}";
                echo "done";
            }
        }

        stage("execute") {
            steps {
                echo "${MESSAGE}";
                echo "done";
                sh 'touch report.txt'
                sh "echo 'build number ${env.BUILD_NUMBER} succeeded' > report.txt"
            }
        }
    }
        post {
            always{
                archiveArtifacts artifacts: 'report.txt', fingerprint: true, onlyIfSuccessful: true

            }
            
        }
}
