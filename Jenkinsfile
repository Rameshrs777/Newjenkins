pipeline {
   agent any
 stages {
       
       stage('terraform version') {
           steps {
               sh """
                    sudo yum install wget unzip;
                    sudo yum install wget -y;
                    wget https://releases.hashicorp.com/terraform/0.12.24/terraform_0.12.24_linux_amd64.zip;
                    sudo unzip ./terraform_0.11.13_linux_amd64.zip -d /usr/local/bin/;
                    terraform -v;
                   """
           }
       }
       
       stage('terraform init') {
           steps {
               sh  """
                   
                   pwd;
         ls;
                   terraform init . ;
                   """
           }
       }
       stage('terraform plan') {
           steps {
               sh  """
                   
                   terraform plan -out=tfplan  ;
                   ls -l ;
                   """
           }
       }
       stage('terraform apply') {
           steps {
               sh  """
                   
                   terraform apply  -auto-approve . ;
                   """
           }
       }
       stage('terraform destroy') {
           steps {
               sh  """
                   
                   terraform destroy -auto-approve . ;
                   """
           }
       }
   }
}
