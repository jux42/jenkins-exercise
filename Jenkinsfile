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
            }
        }
    }
        post {
 
                env.MESSAGE = "finished"
                echo "${env.MESSAGE}";

                sh 'touch report.txt'

                sh "echo 'build number ${env.BUILD_NUMBER} succeeded' > report.txt"

                // Archiver le fichier généré
                archiveArtifacts artifacts: 'report.txt', fingerprint: true, onlyIfSuccessful: true
            }
        }
    }

