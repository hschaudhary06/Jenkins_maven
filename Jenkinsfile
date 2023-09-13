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
    }
}
