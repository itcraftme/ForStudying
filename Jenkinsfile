pipeline
{
    agent any
    tools{
        jdk 'JDK'
    }
    parameters{
        string(name: "VERSION", defaultValue:"" , description:"this is the version name")
        choice(name: "VERSION", choices:['1.1.0','1.2.0','1.3.0'], description:"choices for versions")
        booleanParam(name: "ExecuteOrNot", defaultValue:true, , description:"to indicate it will be executed or not")
    }
    environment 
    {
        NewVersion = "Yan_1.0"
        ServerCredential = credentials('ServerCred')
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
            when{
                expression{
                    params.ExecuteOrNot
                }
            }
             steps
            {
                echo "this is the credential for server ${ServerCredential}"
                withCredentials([
                    usernamePassword(credentials:'ServerCred',usernameVariable:USER,passwordVariable:PWD)
                ]){
                    sh "some script ${USER} ${PWD}"
                }
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
