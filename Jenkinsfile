#!groovy

@Library('MJS@master') _

pipeline {
	agent any

  	environment {
       		APP_NAME= 'pki-billing-ms'
		RPM_NAME="${APP_NAME}-${BUILD_DATE}-1.git.${GIT_COMMIT}.x86_64.rpm"
	}

	stages {

        	stage('Prep Env') {
            		steps {
                		echo 'Prep Env..'
				appEnv()
				getEnv()
				preStage()
				echo "${env.YUM_URL}"
        			echo "${env.DEV_REPO}"
				echo "${env.TEST_REPO}"
				echo "${env.SALT_MASTER}"
				echo "${env.RPM_PATH_BASE}"
				echo "${env.BUILD_DATE}"
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
