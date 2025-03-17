pipeline {
  agent any
    	tools {
		maven "mvn"
       	}
environment {
    DOCKERHUB_CREDENTIALS=credentials('dockerhub')
    AWS_DEFAULT_REGION = 'ap-south-1'
    BUILD_NUMBER = "${env.BUILD_NUMBER}"
  }
  stages {
    stage("Maven Build") {
      steps {
        script {
          sh "mvn clean install -DskipTests"
        }
      }
    }
 stage("Build & Push Docker Image") {
      steps {
        script {
          sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-161Fa12014'
          sh "docker build -t katamreddy/mavencicd:$BUILD_NUMBER ."
          sh "docker push katamreddy/mavencicd:$BUILD_NUMBER"
        }
      }
    }	  
}
}
