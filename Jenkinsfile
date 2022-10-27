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
        cicd.newDeploy("${env.WORKSPACE}"),"172.31.20.104","testapp".war')
    }
    stage('ContinuousTesting_master')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        cicd.runselenium("${env.WORKSPACE}")
    }
    stage('ContinuousDelivery_master')
    {
        cicd.newdeploy("${env.WORKSPACE}"),"172.31.18.153","prodapp".war')
    }
}
