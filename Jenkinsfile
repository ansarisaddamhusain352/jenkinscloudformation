pipeline {
    agent any
	parameters {
		string defaultValue: 'Jenkinsfile', description: '', name: 'JenkinsFileParameter'
		boolean value: false, description: '', name: 'override_existing_code'
		choice choices: ['dev','qa','prod'], description: '', name: 'deploy'
	}
    stages {
        stage('Build') {
            steps {
				echo "deploy environment: $deploy"
				echo "is override code : $override_existing_code"
                sh "export AWS_DEFAULT_REGION=us-east-1"
				sh "aws cloudformation update-stack --stack-name myteststack --template-body file://config.json --region 'us-east-1'"
            }
        }
        stage('Test') {
            steps {
                echo "deploy environment: $deploy"
            }
        }
        stage('Deploy') {
            steps {
                sh "ls"
            }
        }
    }
}