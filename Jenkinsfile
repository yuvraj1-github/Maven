pipeline {

	agent any
	stages {
	
		stage ('SCM chekout') {
		
			steps {
			
				git branch: 'main', credentialsId: 'GitHub', url: 'https://github.com/yuvraj1-github/Maven.git'
			}
		}
		
		stage ('maven compile') {
		
		steps {
			withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
			sh 'mvn compile'
			}
				
			}
		}
		
		stage ('maven test') {
			steps {
			
				withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
			sh 'mvn test'
				}
			
			}
			stage ('maven pakage') {
				steps {
					withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
			sh 'mvn package'
				}
					
				}
			
			}
		
		}
	
	}
}