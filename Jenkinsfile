#!groovy

@Library('MJS@master') _

pipeline {
	agent any

	stages {

        	stage('Prep Env') {
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

        	stage('Maven Build') {
            		steps {
                		echo 'Maven Build...'
				echo env.GIT_COMMIT
            		}
        	}	

        	stage('SonarQube') {
            		steps {
				SonarQAnalysis(env.GIT_BRANCH)
            		}
        	}

        	stage('QA Gate') {
            		steps {
                		echo 'QA Gate....'
            		}
        	}

        	stage('RPM') {
            		steps {
                		echo 'Deploying RPM....'
            		}
        	}	

        	stage('Deploy Dev') {
            		steps {
                		echo 'Deploying Dev....'
            		}
        	}

        	stage('Deploy Test') {
            		steps {
                		echo 'Deploying Test....'
            		}
        	}

    	}
}
