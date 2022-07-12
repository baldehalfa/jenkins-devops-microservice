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
	agent {
		docker {
			// image 'maven:3.8.6'
			image 'node:18.5'
		}
	}
	stages {
		stage('Build') {
			steps {
				// sh 'mvn --version'
				sh 'node --version'
				echo "Build"
			}
		}
		stage('Test') {
			steps {
				echo "Test"
			}
		}
		stage('Integration Test') {
			steps {
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