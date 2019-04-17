#!groovy

@Library('MJS') _

pipeline {
	agent any

  	environment {
		BUILD_DATE=new Date().format( 'yyyyMMddHHmm' )

	}

	stages {

		preStage()

        	stage('Prep Env') {
            		steps {
                		echo 'Prep Env..'
				getEnv()
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
