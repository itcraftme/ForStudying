pipeline
{
    agent any
    environment 
    {
        NewVersion = "1.0"
    }
    stages
    {
        stage("setup")
        {
            when{
                expression {
                    BRANCH_NAME == 'main'
                }
            }
            steps
            {
                echo "I am changing the pipeline code only for main "
                echo "this is a set up process ${NewVersion}"
            }
        }
        stage("test")
        {
             steps
            {
                echo "8th build, this is test"
            }
        }
        stage("clearup")
        {
            steps
            {
                echo "this is cleanup"
            }
        }
    }
    post
    {
        always{echo "always output this"}
        failure{echo "test failed"}
        success{echo "test succeed"}
    }
}
