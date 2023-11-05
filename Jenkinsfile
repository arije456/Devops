pipeline {
	agent any

	stages {

		stage('Build'){
			steps {
				sh "mvn clean package -DskipTests=true"
				archive 'target/*.jar'
			}
		}

		stage('Test'){
			steps{
				sh "mvn test"
			}
			post{
				always{
					junit 'target/test-report/*.xml'
				}
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
