node('QA') {
	def responses = null
	stage('selection') {
		responses = input message: "Enter Branch and Build Type",
		parameters: [string(defualtValue: '',description: 'Enter Branch Name' , name: 'BRANCH_NAME'),
			    choice(choices:'DEBUG\nRELEASE' , description: 'Select choice', name: 'BUILD_TYPE')]
	}
	stage('git') {
		git 'https://github.com/mrk9676/Learning_Jenkins.git'
	}
	stage('build') {
		if (responses.BUILD.TYPE == 'DEBUG')
			sh 'mvn clean package'
		if (response.BUILD.TYPE == 'RELEASE')
			sh 'mvn install' 
	}
	stage('testresults'){
		junit 'gameoflife-web/taget/surefire-reports/*.xml'
	}
	stage('artifacts'){
	archiveArtifacts artifacts: 'gameoflife-web/target/*.war'
	}
}
	

