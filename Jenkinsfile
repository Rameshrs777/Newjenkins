node {
env.PATH += ":/opt/terraform_0.7.13/"


 stage ('Terraform Plan') {
 sh 'terraform plan -no-color -out=create.tfplan'
}

// Optional wait for approval
input 'Deploy stack?'

stage ('Terraform Apply') {
sh "terraform --version"
}
