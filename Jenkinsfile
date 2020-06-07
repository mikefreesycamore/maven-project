pipeline {
	agent any
	tools {
		jdk  'jdk_1.8.0_251'
	}
	stages{
		stage('Build'){
			steps {
				bat 'maven.bat'
			}
			post {
				success {
					echo ' Now Archiving...'
					archiveArtifacts artifacts: '**/target/*.war'
				}
			}
		}
	}
}
