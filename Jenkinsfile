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
	environment{
		PATH="/var/lib/jenkins/anaconda3/bin:$PATH"
	}
	stages{
	stage("Code pull"){
		steps{
			checkout scm
		}
	}
	stage('Build enviroment'){
		steps{
			echo "Hola Ruben"
			sh '''conda create --yes -n ${BUILD_TAG} python
			      echo "Espacio entre conda y source"
			      source activate ${BUILD_TAG}
			      pip install -r requirements.txt
			   '''
			
		}
	}
	stage('Test environment'){
		steps{
			echo "Estas en produccion"
		}
	}
	}
	
	post{
		always{
			sh 'conda remove --yes -n ${BUILD_TAG} --all'
		}
		failure{
			echo "Send e-mail, when failed"
		}
	}
}
