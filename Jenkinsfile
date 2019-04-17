#!groovy

pipeline {
	agent any

  	environment {
		BUILD_DATE=new Date().format( 'yyyyMMddHHmm' )

	}

	stages {

        	stage('Prep Env') {
            		steps {
                		echo 'Prep Env..'
            		}		
        	}	

        	stage('Maven Build') {
            		steps {
                		echo 'Maven Build...'
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
