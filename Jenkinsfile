pipeline {
	agent any
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
