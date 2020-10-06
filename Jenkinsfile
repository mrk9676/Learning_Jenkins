node('QA') {
    try {
        def responses = null
        stage('selection'){
            responses = input message: 'Enter branch and select build type',
            parameters: [name: 'BRANCH_NAME', string(defaultValue: '', description: 'Enter the branch'),
                        choice(name: 'BUILD_TYPE', choices: 'DEBUG\nRELEASE', description: 'BUILD Type')]

        }

        stage('git') {
            git 'https://github.com/mrk9676/Learning_Jenkins.git'
        }
        stage('build') {
            if (responses.BUILD_TYPE == 'DEBUG'){
                sh 'mvn clean package'
            }
            if (responses.BUILD_TYPE == 'RELEASE'){
                sh 'mvn clean install'
            }
            
            
        }
        stage('testresults'){
            junit 'gameoflife-web/target/surefire-reports/*.xml'
        }
        stage('archiveartifacts') {
            archiveArtifacts artifacts: 'gameoflife-web/target/*.war', followSymlinks: false
        }
        currentBuild.result = 'SUCCESS'

    }
    catch(err) {
        currentBuild.result = 'FAILURE'
    }
    finally {
		echo " Build succeded"
    }
    
}
