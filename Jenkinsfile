pipeline{
    agent any
    
    environment{
        MESSAGE = "main message"

    }
    stages{
        stage("check"){
        environment{
        MESSAGE = "check messsage"}
            steps{
            echo "$MESSAGE";
            }
            {
            echo "done";
            
            }
        
        }
        stage("execute"){
        steps{
        echo "$MESSAGE";
                 }{
        echo "done";}
        }
        stage("post"){
        environment{
        MESSAGE = "finished"}
        steps{
            file: '${env.WORKSPACE/report.txt}'
        }
        {
        echo MESSAGE;
        echo "build number $env.BUILD_NUMBER succeeded" | tee report.txt
        }
    
    }
}
