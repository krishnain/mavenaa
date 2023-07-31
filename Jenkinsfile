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
                deploy adapters: [tomcat9(credentialsId: '06980228-45ae-4423-8f80-12b3f2dfb6b1', path: '', url: 'http://172.31.16.88:8080')], contextPath: 'mytestapp', war: '**/*.war'
            }
        }
        stage('Conttesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipleine1/testing.jar'
            }
        }
        stage('ContDelivery')
        {
            steps
            {
              deploy adapters: [tomcat9(credentialsId: '06980228-45ae-4423-8f80-12b3f2dfb6b1', path: '', url: 'http://172.31.22.249:8080')], contextPath: 'myprodapp', war: '**/*.war'
            }
        }
    }
}
