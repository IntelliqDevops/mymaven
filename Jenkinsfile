@Library('mylibrary')_
pipeline
{
    agent any
    stages
    {
        stage('ContDownload_Master')
        {
            steps
            {
                script
                {
                    cicd.gitDownload("maven")
                }
            }
        }
        stage('ContBuild_Master')
        {
            steps
            {
                script
                {
                    cicd.mavenBuild()
                }
            }
        }
        stage('ContDeployment_Master')
        {
            steps
            {
                script
                {
                    cicd.tomcatDeploy("DeclarativePipelinewithSharedLibraries","172.31.22.134","testapp")
                }
            }
        }
        stage('ContTesting_Master')
        {
            steps
            {
                script
                {
                    cicd.gitDownload("FunctionalTesting")
                    cicd.executeSelenium("DeclarativePipelinewithSharedLibraries")
                }
            }
        }
        stage('ContDelivery_Master')
        {
            steps
            {
                script
                {
                    cicd.tomcatDeploy("DeclarativePipelinewithSharedLibraries","172.31.31.139","prodapp")
                }
            }
        }
    }
}
