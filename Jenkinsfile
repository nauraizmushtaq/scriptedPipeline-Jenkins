pipeline {
    agent any
    stages {
	
	stage('Build') {
	    agent {
                        label "master"
                }
        steps {
	       
               sh 'bash "Build.sh"'
                }
        }

	
        stage('Unit') {
            parallel {
                stage('Test On Windows') {
                    agent {
                        label "master"
                    }
                    steps {
                        sh 'bash "Unit.sh"'
                    }
                    
                }
                stage('Test On Master') {
                    agent {
                        label "master"
                    }
                    steps {
			
			  sh 'bash "Deploy.sh"'
					}
                }
            }
        }
    }
}
