pipeline {

	agent any
	stages {
	
		stage ('SCM chekout') {
		
			steps {
			
				git branch: 'main', credentialsId: 'GitHub', url: 'https://github.com/yuvraj1-github/Maven.git'
			}
		}
		stage ('maven clean') {
			steps {
			withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
			sh 'mvn clean'
			}
				
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
		
		}
		stage ('maven pakage') {
			steps {
				withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
			sh 'mvn package'
				}
			
			}
		
		}
		stage ('Deploy to tomcat') {
		
			steps {
			
			deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'Tomcat', path: '', url: 'http://localhost:9090/')], contextPath: 'myapp', war: 'webapp\\target\\webapp.war'
			}
		}
	
	}
}