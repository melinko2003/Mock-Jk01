#!groovy

@Library('MJS@master') _

pipeline {
	agent any

  	environment {
		env('test')
	}

	stages {

        	stage('Prep Env') {
            		steps {
                		echo 'Prep Env..'
				getEnv()
				preStage()
				echo "${YUM_URL}"
        			echo "${DEV_REPO}"
				echo "${TEST_REPO}"
				echo "${SALT_MASTER}"
				echo "${RPM_PATH_BASE}"
				echo "${APP_NAME}"
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
                		echo 'SonarQube....'
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
