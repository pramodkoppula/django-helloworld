pipeline {
agent{
    node {
        label 'master'
        customWorkspace '/var/www/JenkinsWorkspace'
    }
   }
 stages {      
          stage ('Checkout') {
		  steps{  
            checkout scm
            
            sh "git clone https://github.com/NHSmastek/NHSD_POC.git"
            sh 'git log HEAD^..HEAD --pretty="%h %an - %s" > GIT_CHANGES'
            //def lastChanges = readFile('GIT_CHANGES')
            //slackSend color: "warning", message: "Started `${env.JOB_NAME}#${env.BUILD_NUMBER}`\n\n_The changes:_\n${lastChanges}"
		}
	  }
         //stage ('Publish results') {
            //slackSend color: "good", message: "Build successful: `${env.JOB_NAME}#${env.BUILD_NUMBER}` <${env.BUILD_URL}|Open in Jenkins>"
	//	}	
    

}
}
