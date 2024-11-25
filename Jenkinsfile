pipeline {
	agent any
	environment {
		DOCKER_IMAGE= 'hello-world-java:latest' //Docker image name
	}
	stages {
		stage('Checkout') {
			steps {
				checkout scm
			}

		}
		stage('Build') {
			steps {
				sh 'javac helloWorld.java'
			}
		}
		stage('Package'){
			steps {
				sh 'jar cf HelloWorld.jar HelloWorld.class'
			}
		}	
		stage('Dcoker Build') {
			steps {
				sh """
				docker build -t $DOCKER_IMAGE .
				"""
			}
		}

	}
	post {
		success {
			echo 'Build completed Successfully'
		}
		failure {
			echo 'Build failed'
		}
		
	}

}

 
