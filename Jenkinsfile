pipeline {
	agent any 
	stages {
		stage ('SCM chekout') {
			git branch: 'main', credentialsId: 'GitHub', url: 'https://github.com/yuvraj1-github/Maven.git'
		}
	}
	stage ('mvn compile') {
		withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
			sh 'compile'
		}
	}
}