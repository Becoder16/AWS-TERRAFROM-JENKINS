pipeline {
  agent any

  environment {
    AWS_REGION = 'us-east-1'
  }

  stages {
    stage('Terraform Init & Apply') {
      steps {
        withCredentials([usernamePassword(
          credentialsId: 'aws-creds', // This is the ID of the AWS credentials you added
          usernameVariable: 'AWS_ACCESS_KEY_ID',
          passwordVariable: 'AWS_SECRET_ACCESS_KEY'
        )]) {
          sh '''
            echo "Initializing Terraform..."
            terraform init -input=false

            echo "Applying Terraform plan..."
            terraform apply -auto-approve
          '''
        }
      }
    }
  }
}
