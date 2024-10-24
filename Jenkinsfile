pipeline {
    agent any

    environment {
        MESSAGE = "main message"
    }

    stages {
        stage("check") {
           
                    
             steps {
                 $MESSAGE = "check message"
                echo "${MESSAGE}";
                echo "done";
            }
        }

        stage("execute") {
            steps {
                echo "${$MESSAGE}";
                echo "done";
            }
        }

        stage("post") {
     
            steps {
                $MESSAGE = "finished"
                echo "${MESSAGE}";
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
    
