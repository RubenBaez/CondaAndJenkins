pipeline{
	agent any

	triggers{
		pollSCM('*/5 * * * 1-5')
	}
	options{
		skipDefaultCheckout(true)
		// Keep the 10 most recent builds
		buildDiscarder(logRotator(numToKeepStr: '10'))
		timestamps()
	}
	enviroment{
		PATH="/var/lib/jenkins/anaconda3/bin:$PATH"
	}
	stages{
	stages("Code pull"){
		steps{
			checkout scm
		}
	}
	stage('Build enviroment'){
		steps{
			echo "Ruben"
		}
	}
	}
}
