pipeline {
	agent any
	tools {
		jdk  'JAVA_HOME'
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
