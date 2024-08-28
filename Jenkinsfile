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
	// agent {docker {image 'maven:3.6.3'}} we can run the pipeline inside a docker image also
	// agent {docker {image 'node:13.8'}}

    // make maven and docker available for buld machine 1st
	environment{
           dockerHome = tool 'myDocker'
		   mavenHome = tool 'myMaven'
		   PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages{
		stage('Build') {
			steps{
				// sh "node --version"
				sh "mvn --version" 
				// sh "docker version"
				echo "Build"
				// Trying to understand the environment variables mentioned in pipeline -> pipeline syntax -> env
				echo "PATH - $PATH" // /opt/java/openjdk/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
				echo "JOB_NAME - $env.JOB_NAME"
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