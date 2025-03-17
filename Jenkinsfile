pipeline {
  agent any
    	tools {
		maven "mvn"
       	}
  stages {
    stage("Maven Build") {
      steps {
        script {
          sh "mvn clean install -DskipTests"
        }
      }
    }        
}
}
