pipeline {
  parameters {
    password (name: 'AKIAVWCRJNBRB7JLSFEZ')
    password (name: 'vBdi5gIJ/0CA/koOBQ446/YP0lKFCFpcOo4pXW/k')
  }
  environment {
    TF_WORKSPACE = 'dev' //Sets the Terraform Workspace
    TF_IN_AUTOMATION = 'true'
    AWS_ACCESS_KEY_ID = "${params.AKIAVWCRJNBRB7JLSFEZ}"
    AWS_SECRET_ACCESS_KEY = "${params.vBdi5gIJ/0CA/koOBQ446/YP0lKFCFpcOo4pXW/k}"
  }
  stages {
    stage('Terraform Init') {
      steps {
        sh "${env.TERRAFORM_HOME}/terraform init -input=false"
      }
    }
    stage('Terraform Plan') {
      steps {
        sh "${env.TERRAFORM_HOME}/terraform plan -out=tfplan -input=false -var-file='dev.tfvars'"
      }
    }
    stage('Terraform Apply') {
      steps {
        input 'Apply Plan'
        sh "${env.TERRAFORM_HOME}/terraform apply -input=false tfplan"
      }
    }
    stage('AWSpec Tests') {
      steps {
          sh '''#!/bin/bash -l
bundle install --path ~/.gem
bundle exec rake spec || true
'''

        junit(allowEmptyResults: true, testResults: '**/testResults/*.xml')
      }
    }
  }
}
