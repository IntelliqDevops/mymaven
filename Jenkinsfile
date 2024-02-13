pipeline
{
    agent any
    stages
    {
        stage('ContDownload')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('ContBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContDeployment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '1ce04ef7-c3a8-44e7-ad81-e6dd8e400a1f', path: '', url: 'http://172.31.81.211:8080')], contextPath: 'newtestapp', war: '**/*.war'
            }
        }
        stage('ContTesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
            
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline1/testing.jar'
            }
        }
        stage('ContDelivery')
        {
            steps
            {
                
                deploy adapters: [tomcat9(credentialsId: '1ce04ef7-c3a8-44e7-ad81-e6dd8e400a1f', path: '', url: 'http://172.31.94.22:8080')], contextPath: 'myprodapp', war: '**/*.war'
            }
        }
    }
}
