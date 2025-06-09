pipeline {
	agent any
	
	tools{
		maven 'MAVEN'
	}
	
	stages{
		stage('Checkout') {
			steps {
				git branch:'master', url:'https://github.com/vsshubhcloud/AnsibleFinal.git'
			}
		}
		
		stage('Build') {
			steps {
				sh 'mvn compile package'
			}
		}
		
		stage('Test') {
			steps {
				sh 'mvn test'
			}
		}
		
		stage('Deploy') {
			steps {
				sh 'ansible-playbook ansible/playbook.yml -i ansible/hosts.ini'
			}
		}
	}
	
	post {
		success{
			echo "Pipeline Successfull!"
		}
		failure{
			echo "Pipeline failed!"
		}
	}
}										
