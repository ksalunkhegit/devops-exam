pipeline {
    agent any  // Run on any available agent

    environment {
        // Define any environment variables needed
        AWS_REGION = "us-east-1"
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning repository'
                git 'https://github.com/ksalunkhegit/devops-exam.git'  // Fetch the latest code
            }
        }

        stage('Terraform Plan') {
            steps {
                echo 'Running Terraform Plan'
                sh 'terraform init'
                sh 'terraform plan'
            }
        }

        stage('Terraform Apply') {
            steps {
                echo 'Applying Terraform Changes'
                sh 'terraform apply -auto-approve'
            }
        }

        stage('Invoke Lambda') {
            steps {
                echo 'Invoking Lambda Function'
                sh 'aws lambda invoke --function-name myLambdaFunction output.txt'  // Example AWS CLI command
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}

