node('QA') {
	properties([pipelineTriggers([cron(['30 12 * * *'])])])
	stage('git'){
	git 'https://github.com/mrk9676/Learning_Jenkins.git'
	}
	stage('build') {
	sh 'mvn clean package'
	}
	stage('testresults'){
	junit 'gameoflife-web/target/surefire-reports/*.xml'
	}
	stage('artifacts'){
	archiveArtifacts artifacts: 'gameoflife-web/target/*.war', followSymlinks: false
	}
	 
}
