pipeline {
    agent any 
    environment {
       
        AWS_REGION = "us-east-1"
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning repository'
                git 'https://github.com/ksalunkhegit/devops-exam.git' 
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
                sh 'aws lambda invoke --function-name myLambdaFunction output.txt' 
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

