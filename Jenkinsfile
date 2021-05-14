
//DECLARATIVE

pipeline {
	agent any

	environment{
		dockerHome = tool "myDocker"
		mavenHome = tool "myMaven"
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Checkout') {
			steps{
				sh 'mvn --version'
				sh 'docker version'
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
		
		stage('Compile') {
			steps{
				sh "mvn clean compile"
			}
		}
		stage('Test') {
			steps{
				sh "mvn test"
			}
		}

		stage('Integration Test') {
			steps{
				sh "mvn failsafe:integration-test failsafe:verify"
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
