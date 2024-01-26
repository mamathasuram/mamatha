pipeline {
    agent any
    
    environment {
        AWS_ACCESS_KEY_ID     = credentials('AKIAT7MEYHFRRK2UDXMI')
        AWS_SECRET_ACCESS_KEY = credentials('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')
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Checkout your source code repository
                    git 'https://github.com/mamathasuram/mamatha.git'
                }
            }
        }

        stage('Terraform Init') {
            steps {
                script {
                    // Initialize Terraform
                    sh 'terraform init'
                }
            }
        }

        stage('Terraform Plan') {
            steps {
                script {
                    // Create a Terraform execution plan
                    sh 'terraform plan -out=tfplan'
                }
            }
        }

        stage('Terraform Apply') {
            steps {
                script {
                    // Apply the Terraform plan
                    sh 'terraform apply -auto-approve tfplan'
                }
            }
        }
    }

    post {
        always {
            // Cleanup steps, such as destroying resources if needed
            script {
                // Destroy the Terraform resources (optional, use with caution)
                // sh 'terraform destroy -auto-approve'
            }
        }
    }
}
