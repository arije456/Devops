pipeline {
	agent any

	stages {

		stage('Build'){
			steps {
				sh "mvn clean package -DskipTests=true"
				archive 'target/*.jar'
			}
		}
		stage('sonarqube'){
			steps{
				withSonarQubeEnv(installationName: 'sonar'){
				sh "mvn sonar:sonar"
				}
			}
		}
	}
}
