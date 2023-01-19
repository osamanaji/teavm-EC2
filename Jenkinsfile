pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'github_cred', url: 'https://github.com/devopsdeepdive/teavm-maven-webapp.git']]])
            }
        }
	stage('Build') {
            steps {
                sh 'mvn compile'
            }
        }
	stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
	stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
	    stage('Hello') {
            steps {
                echo "Hello World for develop branch"
            }
        }
	   /* stage('Deploy') {
            steps {
               sshagent(['tomcat_server']) {
		sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/teavm-maven-webapp/target/teavm-maven-webapp-1.0-SNAPSHOT.war ubuntu@35.171.157.31:/opt/apache-tomcat-8.5.84/webapps'
			}
            }
        } */
	/* stage('Notify') {
            steps {
		    if {
			    slackSend channel: '#devopsdeepdive_batch3', message: 'Build is successful', teamDomain: 'devopsdeepdivebatch', tokenCredentialId: 'slack_batch12' 
            }
		 else {
			 slackSend channel: '#devopsdeepdive_batch3', message: 'Build is failed', teamDomain: 'devopsdeepdivebatch', tokenCredentialId: 'slack_batch12'
		 }
	 }
        } */
    }
}
