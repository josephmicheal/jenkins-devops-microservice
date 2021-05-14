
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
