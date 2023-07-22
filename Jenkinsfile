pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from GitHub repository
                git 'https://github.com/iknoorsinghchuni/jenkinslambda.git'
            }
        }
        
        stage('Build') {
            steps {
                // Package the code into a deployment package
                sh 'zip -r demojenkins.zip *'
            }
        }

        stage('Deploy to AWS Lambda') {
            environment {
                AWS_DEFAULT_REGION = 'us-east-1'
                LAMBDA_FUNCTION_NAME = 'jenkinslambda1'
            }
            steps {
                // Deploy the Lambda function using AWS CLI
                sh "aws lambda update-function-code --function-name $LAMBDA_FUNCTION_NAME --zip-file fileb://lambda_function.zip --region $AWS_DEFAULT_REGION"
            }
        }
    }
}
