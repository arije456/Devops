pipeline {
	agent any

	stages {

		stage('Build'){
			steps {
				sh "mvn clean install -DskipTests"
			}
		}

		stage('Test'){
			steps{
				sh "mvn test"
			}
		}
        
		stage('sonarqube'){
			steps{
				withSonarQubeEnv(installationName: 'sonar'){
				sh "mvn clean sonar:sonar"
				}
			}
		}
	}
}
