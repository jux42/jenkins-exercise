pipeline {
    agent any

    environment {
        MESSAGE = "main message"
    }

    stages {
        stage("check") {
           
                    
             steps {
                 env.MESSAGE = "check message"
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

        stage("post") {
     
            steps {
                env.MESSAGE = "finished"
                echo "${env.MESSAGE}";
            }
        }
    }
            }post{
                always{
                sh 'touch report.txt';
                sh "echo 'build number ${env.BUILD_NUMBER} succeeded' > report.txt"
                archiveArtifacts allowEmptyArchive: true,
                                 artifacts: '*.txt',
                                 fingerprint: true,
                                 onlyIfSuccessful: true
                }
            }
    
