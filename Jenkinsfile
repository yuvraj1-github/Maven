pipeline {

    agent any

    stages {

        stage('SCM checkout') {
            steps {
                git branch: 'main', credentialsId: 'GitHub', url: 'https://github.com/yuvraj1-github/Maven.git'
            }
        }

        stage('maven clean') {
            steps {
                withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
                    sh 'mvn clean'
                }
            }
        }

        stage('maven compile') {
            steps {
                withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
                    sh 'mvn compile'
                }
            }
        }

        stage('maven test') {
            steps {
                withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
                    sh 'mvn test'
                }
            }
        }

        stage('maven package') {
            steps {
                withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
                    sh 'mvn package'
                }
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                step([$class: 'DeployPublisher',
                    war: '**/target/webapp.war',
                    contextPath: 'webapp',
                    adapters: [[
                        $class: 'Tomcat9xAdapter',
                        credentialsId: 'TOMCAT',
                        url: 'http://localhost:9090/manager/html'
                    ]]
                ])
            }
        }

    } 

}
