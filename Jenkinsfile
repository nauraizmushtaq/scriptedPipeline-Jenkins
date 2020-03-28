pipeline {
    agent any
    stages {
	
	stage('Build') {
	    agent {
                        label "master"
                }
        steps {
		cd "scriptedPipeline-Jenkins"
                bat "Build.bat"
                }
        }

	
        stage('Unit') {
            parallel {
                stage('Test On Windows') {
                    agent {
                        label "master"
                    }
                    steps {
                        bat "Unit.bat"
                    }
                    
                }
                stage('Test On Master') {
                    agent {
                        label "master"
                    }
                    steps {
			
			  bat "Deploy.bat"
					}
                }
            }
        }
    }
}
