pipeline
{
    agent any
	tools
	{
	 jdk 'JAVA_HOME'
	 maven 'MAVEN_HOME'
	}
    stages
    {
        stage('ContDownload')
        {
            steps
            {
                checkout scm
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
              sshPublisher(publishers: [sshPublisherDesc(configName: 'tomcat-server', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '/opt/apache-tomcat-8.5.43/bin/startup.sh', execTimeout: 120000, flatten: true, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '/opt/apache-tomcat-8.5.43/webapps/', remoteDirectorySDF: true, removePrefix: 'target', sourceFiles: '**/*.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
	    }    
	}
    }
}
