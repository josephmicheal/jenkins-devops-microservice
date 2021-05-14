
//DECLARATIVE

pipeline {
	agent {
		docker { image 'maven:3.6.3'}
	}
	stages {
		stage('Build') {
			steps{
				sh 'mvn --version'
				echo "Build"
				input 'This is input string'
				echo 'Environment Variables'
				echo "PATH - $PATH"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"

			}
		}
		
		stage('Test') {
			steps{
				echo "Test"
			}
		}

		stage('Integration Test') {
			steps{
				echo "Integration Test"
			}
		}
	}

	// After build we can have kind of alert to send mail or do some final thing
	post {
		always{
			echo 'Build status alert always'
		}
		success{
			echo 'Build is successfull'
		}
		failure{
			echo 'Build is failed'
		}
		changed{
			echo 'Build status changed compared with previous build'
		}
		unstable{
			echo 'Some test cases are failed'
		}
	}
}
