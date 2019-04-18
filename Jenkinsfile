#!groovy

@Library('MJS@master') _

pipeline {
	agent any

	stages {
        	stage('Prepare environment') {
            		steps {
                		echo 'Prep Env..'
				appEnv('pki-billing-ms')
				getEnv()
				preStage()
				echo "${YUM_URL}"
        			echo "${DEV_REPO}"
				echo "${TEST_REPO}"
				echo "${SALT_MASTER}"
				echo "${RPM_PATH_BASE}"
				echo "${RPM_NAME}"
				echo "${APP_NAME}"
				echo "${BUILD_DATE}"
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
              			expression { env.GIT_BRANCH == "master" }
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

