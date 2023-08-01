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
        stage('ContDeployement')
        {
            steps
            {
                 deploy adapters: [tomcat9(credentialsId: '4522c3bd-1bf9-48cb-862e-26c5fd7ca34c', path: '', url: 'http://hyd1vtestqa:8080')], contextPath: 'rahultestapp', war: '**/*.war'
            }
        }
        stage('ContTesting')
        {
            steps
            {
                 git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                 sh 'java -jar /var/lib/jenkins/workspace/Declarativepipeline2/testing.jar'
            }
        }
        stage('ContDelivery')
        {
            steps
            {
                 deploy adapters: [tomcat9(credentialsId: '4522c3bd-1bf9-48cb-862e-26c5fd7ca34c', path: '', url: 'http://hyd1vtestprod:8080')], contextPath: 'rahulprodapp', war: '**/*.war'
            }
        }
        
    }
}
