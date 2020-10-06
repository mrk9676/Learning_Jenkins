node('QA') {
	def resourses = null
	stage('selection') {
		responses = input message: 'Enter build type and branch name',
		parameters: [string(name:'BRANCH_NAME',defaultValue:'',description:'Enter Branch Namei'),
			     choice(name:'BUILD_TYPE',choices:'DEBUG\nRELEASE',description:'Enter Build Type')]
	}
	stage('git') {
	git 'https://github.com/mrk9676/Learning_Jenkins.git'
	}
	if (responses.BRANCH_TYPE == 'DEBUG') {
		sh 'mvn clean package'
	}
	if ('response.BRANCH_TYPE == 'RELEASE') {
		sh 'mvn clean install'
	}
	stage('testcases') {
	junit 'gameoflife-web/target/surefire-reports/*.xml'
	}
	stage('Artifacts') {
	archiveArtifacts artifacts: 'gameoflife-web/target/*.war'
	}
}
