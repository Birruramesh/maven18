node('built-in')
{
    stage('ContinuousDownload_master')
    {
        git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('ContinuousBuild_master')
    {
        sh 'mvn package'
    }
    stage('ContinuousDeployment_master')
    {
       deploy adapters: [tomcat9(credentialsId: '8cc7d40a-bab0-438d-8dc2-f0d886815228', path: '', url: 'http://172.31.16.84:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('ContinuousTesting_master')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar'
    }
    stage('ContinuousDelivery_master')
    {
        input message: 'Need approvals from the DM!', submitter: 'srinivas'
        deploy adapters: [tomcat9(credentialsId: '8cc7d40a-bab0-438d-8dc2-f0d886815228', path: '', url: 'http://172.31.29.58:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
    
    
    
    
    
}
