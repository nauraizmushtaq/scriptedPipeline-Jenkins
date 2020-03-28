pipeline {
    agent any
    stages {
	
	stage('Build') {
	    agent {
                        label "master"
                }
        steps {
		git https://github.com/nauraizmushtaq/scriptedPipeline-Jenkins.git
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
