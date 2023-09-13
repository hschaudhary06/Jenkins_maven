pipeline {
    agent any 
    stages {
        stage('Cleanig Stage') { 
            steps {
                 bat "mvn clean"
            }
        }
        stage('Testing Stage') { 
            steps {
                 bat "mvn test"
            }
        }
        stage('Packaging Stage') { 
            steps {
                 bat "mvn package"
            }
        }
	stage('Consolidate Results') {
	    steps {
	    	input("DO you want to capture results?")
		junit'**/target/surefire-reports/TEST-*.xml'
		archive'target/*.jar'
	    }
	}
	stage('Email Build Status') {
	    steps {
	    	mail body: '${evn.JOB_NAME} - Build#${env.BUILD_NUMBER} - ${currentBuild.currentResult}\n\nCheck console output at ${env.BUILD_URL} to view the results.', subject: '${env.JOB_HOME} - Build#${env.BUILD_NUMBER} - ${currentBuild.currentResult}!!', to: 'hs.tech025@gmail.com'
	    }
	}
    }
}
