pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				//git '/home/JenkinsDependencyCheckTest'
				//git branch:'master', url: 'https://github.com/ScaleSec/vulnado.git'
				git branch:'master', url: 'https://github.com/lemonjin1997/JenkinsDependencyCheckTest.git'
			}
		}

		stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'Default'
				//dependencyCheck additionalArguments: '--format HTML --format XML --suppression suppression.xml', odcInstallation: 'Default'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}
