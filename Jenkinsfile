pipeline {
agent{
    node {
        label 'master'
        customWorkspace '/var/www/NHSDPOC_CICD'
    }
   }
 stages {      
          stage ('Checkout') {
		  steps{  
            checkout scm
            
            //sh "git clone https://github.com/NHSmastek/NHSD_POC.git"
            sh 'git log HEAD^..HEAD --pretty="%h %an - %s" > GIT_CHANGES'
            //def lastChanges = readFile('GIT_CHANGES')
            //slackSend color: "warning", message: "Started `${env.JOB_NAME}#${env.BUILD_NUMBER}`\n\n_The changes:_\n${lastChanges}"
		}
	  }
         stage ('Test') {
		 steps {
            	//sh "cd /var/www/NHSDPOC_CICD/NHSD_POC"
		sh "/var/www/NHSDPOC_CICD/NHSD_POC/NHSD-env/bin/activate"
	        sh "pytest -v /var/www/NHSDPOC_CICD/NHSD_POC/NHS.Automation/FrameworkPython/test_cases/poc_test_cases.py "
		sh "pytest -v poc_test_cases.py"
		}	
	 }

}
}
