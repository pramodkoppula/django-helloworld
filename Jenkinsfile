pipeline {
agent any{
    //node {
        label 'my-defined-label'
        customWorkspace '/var/www/JenkinsWorkspace'
    //}
   }
 stages {      
  try {
        stage ('Checkout') {
            
            //checkout scm
            //sh 'cd /var/www/JenkinsWorkspace'
            //git clone https://github.com/pramodkoppula/django-helloworld.git
            //sh 'git log HEAD^..HEAD --pretty="%h %an - %s" > GIT_CHANGES'
            //def lastChanges = readFile('GIT_CHANGES')
            //slackSend color: "warning", message: "Started `${env.JOB_NAME}#${env.BUILD_NUMBER}`\n\n_The changes:_\n${lastChanges}"
		}	
         stage ('Publish results') {
            //slackSend color: "good", message: "Build successful: `${env.JOB_NAME}#${env.BUILD_NUMBER}` <${env.BUILD_URL}|Open in Jenkins>"
		}	
    }

    catch (err) {
        //slackSend color: "danger", message: "Build failed :face_with_head_bandage: \n`${env.JOB_NAME}#${env.BUILD_NUMBER}` <${env.BUILD_URL}|Open in Jenkins>"

        throw err
    }

}
}
