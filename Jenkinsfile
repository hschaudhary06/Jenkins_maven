pipeline {
    agent any 
    stages {
        stage('Parallel Execution') {
	    steps {
	    	parallel (
		  a:{
		    bat 'mvn clean'
		  },
		  b:{
		    bat 'mvn test'
		  },
		  c:{
		    bat 'mvn package'
		  }
		)
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
