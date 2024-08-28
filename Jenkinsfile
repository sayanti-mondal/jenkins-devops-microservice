// Scripted pipeline:-
// node {
// 	stage('Build') {
// 		echo "Build"
// 	}
// 	stage('Test') {
// 		echo "Test"
// 	}
//     stage('Integration Test') {
// 		echo " Integration Test"
// 	}
// }

// node {
// 	echo "Build"
// 	echo "Test"
//     echo " Integration Test"
// 	}

//  above code is known as a scripted pipeline code, where node refers to a machine that runs the pipelines. we can divide the run of a 
//  pipeline in multiple stages. In scripted stage blocks are optional.

// Declarative pipeline
pipeline{
	agent any
	stages{
		stage('Build') {
			steps{
				echo "Build"
				}
			}
		stage('Test') {
			steps {
				echo "Test"
				}
			}
		stage('Integration Test') {
			steps{
			echo "Integration Test"
			}
		}
	}

	post{
		always {
			echo 'This block always runs'
		}
		success {
			echo 'This block runs when build is successful'
		}
		failure {
			echo 'This block runs when build fails'
		}
	}
}