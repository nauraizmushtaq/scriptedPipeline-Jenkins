pipeline {
    agent any
    stages {
	
	stage('Build') {
	    agent {
                        label "master"
                }
        steps {
	       checkout scm
               bash "Build.sh"
                }
        }

	
        stage('Unit') {
            parallel {
                stage('Test On Windows') {
                    agent {
                        label "master"
                    }
                    steps {
                        bash "Unit.sh"
                    }
                    
                }
                stage('Test On Master') {
                    agent {
                        label "master"
                    }
                    steps {
			
			  bash "Deploy.sh"
					}
                }
            }
        }
    }
}
