def call() {

  def LABEL = "jenkins-agent-pod-${UUID.randomUUID().toString()}"

  pipeline {
    agent {
      kubernetes {
        cloud 'openshift'
        inheritFrom "maven-sdc"
        defaultContainer 'jnlp'
        label "${LABEL}"
      }
    }
    	options {
      		gitLabConnection('gitlab')
    	}

    	environment {
      		NEXUS_AUTH = credentials('cicd-nexus-credentials')
      		NEXUS_USERNAME = "${NEXUS_AUTH_USR}"
      		NEXUS_PASSWORD = "${NEXUS_AUTH_PSW}"
      		SONAR_TOKEN = credentials('cicd-sonar-token')
    	}

    	stages {
      		stage('performance-test Test') {
        		steps {
          			echo "==== Download dependencies Stage ===="
                updateGitlabCommitStatus name: 'download-dependencies', state: 'running'
                echo "==== Execute jmeter ===="
                sh "chmod +x apache-jmeter-5.2.1/bin/jmeter.sh"
                sh "apache-jmeter-5.2.1/bin/jmeter.sh -n -t PCC/PCC.jmx"

        		}
        		post {
          			failure {
           				updateGitlabCommitStatus name: 'performance-test', state: 'failed'
          			}
          			success {
            			updateGitlabCommitStatus name: 'performance-test', state: 'success'
          			}
        		}
      		}
			stage('reports') {
				steps {
					dir("${DIR}") {
						script {
							allure([
								includeProperties: false,
								jdk: '',
								properties: [],
								reportBuildPolicy: 'ALWAYS',
								results: [[path: 'allure-results']]
							])
						}
					}
				}
			}
    	}
	}
}
call()
