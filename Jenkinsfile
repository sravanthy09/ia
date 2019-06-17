pipeline{
  agent any
  
  stages {
    stage('pull code from github'){
      steps{
        git branch: 'master', url: 'https://github.com/sravanthy09/ia'
      }
    }
    
    stage('Setup terraform path'){
      steps{
        script{
          def terraformHome =tool name: 'Terraform'
          env.PATH = "${terraformHome}:${env.PATH}"
        }
        
        sh 'terraform --version'
      }
    }
    
    stage('Deploy infrastructure'){
      steps{
        dir('vpc-tf'){
          sh 'terraform init'
          sh 'terraform destroy -auto-approve'
        } 
      }
    }
  }
}
