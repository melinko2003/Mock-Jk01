#!groovy

@Library('MJS@master') _

pipeline {
	agent any

	stages {

        	stage('Prep Env') {
            		steps {
                		echo 'Prep Env..'
				app-env()
				getEnv()
				preStage()
				echo "${env.YUM_URL}"
        			echo "${env.DEV_REPO}"
				echo "${env.TEST_REPO}"
				echo "${env.SALT_MASTER}"
				echo "${env.RPM_PATH_BASE}"
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
