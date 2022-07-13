//SCRIPTED METHOD
// node {
// 	echo "Build"
// 	echo "Test"
// 	echo "Integration Test"
// }

//DECLARATIVE METHOD
// pipeline {
// 	agent any
// 	stages {
// 		stage('Build') {
// 			steps {
// 				echo "Build"
// 			}
// 		}
// 		stage('Test') {
// 			steps {
// 				echo "Test"
// 			}
// 		}
// 		stage('Integration Test') {
// 			steps {
// 				echo "Integration Test"
// 			}
// 		}
// 	} 
// 	post {
// 		always {
// 			echo "I am awesome. I always run."
// 		}
// 		success {
// 			echo "I run when you are successful."
// 		}
// 		failure {
// 			echo "I run when you fail."
// 		}
// 	}
// }

// usung docker image 
pipeline {
	// agent {
	// 	docker {
	// 		// image 'maven:3.8.6'
	// 		// image 'node:18.5'
	// 	}
	// }
	agent any
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
		// name 'my-env'
		// url 'http://my-env.com'
	}
	stages {
		stage('Checkout') {
			steps {
				sh 'mvn --version'
				sh 'docker version'
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage('Compile') {
			steps {
				sh "mvn clean compile"
				echo "Test"
			}
		}
		stage('Test') {
			steps {
				sh "mvn test"
				echo "Test"
			}
		}
		stage('Integration Test') {
			steps {
				sh "mvn failsafe:integration-test failsafe:verify"
				echo "Integration Test"
			}
		}
	} 
	post {
		always {
			echo "I am awesome. I always run."
		}
		success {
			echo "I run when you are successful."
		}
		failure {
			echo "I run when you fail."
		}
	}
}