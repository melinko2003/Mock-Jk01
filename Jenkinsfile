#!groovy

@Library('MJS@master') _

pipeline {
	agent any

  	environment {
       		APP_NAME= 'pki-billing-ms'
		BUILD_DATE= new Date().format( 'yyyyMMddHHmm' )
		RPM_NAME="${APP_NAME}-${BUILD_DATE}-1.git.${GIT_COMMIT}.x86_64.rpm"
	}

	stages {

        	stage('Prep Env') {
            		steps {
                		echo 'Prep Env..'
				appEnv()
				getEnv()
				preStage()
				echo "${YUM_URL}"
        			echo "${DEV_REPO}"
				echo "${TEST_REPO}"
				echo "${SALT_MASTER}"
				echo "${RPM_PATH_BASE}"
				echo "${RPM_NAME}"
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
