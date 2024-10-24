pipeline {
    agent any

    environment {
        MESSAGE = "main message"
    }

    stages {
        stage("check") {
            steps {
                script {
                    env.MESSAGE = "check message"
                }
                echo "${env.MESSAGE}";
                echo "done";
            }
        }

        stage("execute") {
            steps {
                echo "${env.MESSAGE}";
                echo "done";
                sh 'touch report.txt'
                sh "echo 'build number ${env.BUILD_NUMBER} succeeded' > report.txt"
            }
        }
    }
        post {
                // Archiver le fichier généré
                archiveArtifacts artifacts: 'report.txt', fingerprint: true, onlyIfSuccessful: true
            }
        }
    

