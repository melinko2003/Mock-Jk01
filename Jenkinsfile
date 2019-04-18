#!groovy

@Library('MJS@master') _

pipeline {
	agent any

	stages {
        	stage('Prepare environment') {
            		steps {
				appEnv('pki-billing-ms')
				getEnv()
				echo "${env.RPM_NAME}"
            		}		
        	}	

        	stage ('Maven Build') {
            		steps {
            			MavenBuild()
			}
        	}	

            	// BEGIN SONAR QUBE
	    	stage ('SonarQube analysis') {
            		steps {
				SonarQAnalysis(env.GIT_BRANCH)
            		}
        	}

        	stage ('Quality Gate') {
            		steps {
                		QAGate(env.GIT_BRANCH)
            		}
        	}

	    	stage ('RPM Build') {
            		when {
              			expression { env.GIT_BRANCH == "origin/master" }
            		}
			steps { 
                                RPMbuild()
                        }
		}
		
        	stage ('Publish/Deploy To Dev') {
            		steps {
                		Deploy2Env(env.RPM_PATH_BASE,env.RPM_NAME,env.DEV_REPO)
            		}
			post{
                                success{
                                        script {
						echo "Success!"
                                                }
                                        }
			}
                }

        	stage ('Publish/Deploy To Test') {
                        steps {
                                Deploy2Env(env.RPM_PATH_BASE,env.RPM_NAME,env.TEST_REPO)
                        }
                        post{
                                success{
                                        script {
                                                echo "Success!"
                                                
                                        }
                                }
                        }
                }

	}
}
