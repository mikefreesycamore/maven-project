pipeline {
	agent any

	parameters {
		string(name: 'tomcat_dev', defaultValue: '3.19.221.237', description: 'Development Server')
		string(name: 'tomcat_prod', defaultValue: '3.25.232.162', description: 'Production Server')
	}

	triggers {
		pollscm('* * * * *')
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

		stage ('Deployments') {
			parallel {
				stage ('Deploy to staging') {
					steps {
						bat 'scp-tomcat-stag.bat'
					}
				}

				stage ('Deploy to production') {
					steps {
						bat 'scp-tomcat-prod.bat'
					}
				}

			}
		}

	}

}

