pipeline {
agent{
    node {
        label 'master'
        customWorkspace '/var/www/NHSDPOC_CICD'
    }
   }
 stages {      
          stage ('Build&Deploy') {
		  steps{  
            checkout scm
            
            //sh "git clone https://github.com/NHSmastek/NHSD_POC.git"
	    //sh "git checkout master"
	    sh """ 
	    cd /var/www/NHSDPOC_CICD
	    git pull"""
	    
            sh 'git log HEAD^..HEAD --pretty="%h %an - %s" > GIT_CHANGES'
            //def lastChanges = readFile('GIT_CHANGES')
            //slackSend color: "warning", message: "Started `${env.JOB_NAME}#${env.BUILD_NUMBER}`\n\n_The changes:_\n${lastChanges}"
		}
	  }
         stage ('Test') {
		 steps {
            	//sh "cd /var/www/NHSDPOC_CICD/NHSD_POC"
		sh """
		cd /var/www/NHSDPOC_CICD/NHSD_POC
		. NHSD-env/bin/activate
	        cd /var/www/NHSDPOC_CICD/NHSD_POC/NHS.Automation/FrameworkPython/test_cases
		pytest -v poc_test_cases.py --html=/var/www/NHSDPOC_CICD/NHSD_POC/Automation_Report/report.html
		emailext attachmentsPattern: '/var/www/NHSDPOC_CICD/NHSD_POC/Automation_Report/report.html', body: 'Find attachments', subject: 'test', to: 'pramod.koppula@mastek.com'"""
		}	
	 }

}
}
