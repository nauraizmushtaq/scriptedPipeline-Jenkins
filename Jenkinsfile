pipeline {
    agent none
    stages {
	
	stage('Build') {
	    agent {
                        label "master"
                }
        steps {
                bat "Build.bat"
                }
        }

	
        stage('Unit-Deploye') {
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
