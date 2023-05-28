pipeline {
    agent any
	parameters {
    string(defaultValue: "TEST", description: 'What environment?', name: 'userFlag')
    choice(choices: ['dev', 'qa', 'prod'], description: 'Select field for target environment', name: 'deploy')
	boolean(value: false, description: 'override existing code?', name: 'override_existing_code')
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