pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/<ksalunkhegit>/devops-exam.git'
            }
        }

        stage('Terraform Plan') {
            steps {
                script {
                    // Initialize Terraform
                    sh 'terraform init'
                    // Run Terraform plan
                    sh 'terraform plan'
                }
            }
        }

        stage('Apply Terraform') {
            steps {
                script {
                    // Apply Terraform changes
                    sh 'terraform apply -auto-approve'
                }
            }
        }

        stage('Invoke Lambda') {
            steps {
                script {
                    // Use AWS CLI to invoke Lambda
                    sh 'aws lambda invoke --function-name myLambdaFunction output.txt'
                }
            }
        }
    }
}
