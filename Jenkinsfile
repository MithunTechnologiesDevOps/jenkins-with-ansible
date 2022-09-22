pipeline {
  agent { 
  label 'ansible'
  }
  environment {
   AWS_EC2_PRIVATE_KEY=credentials('ec2-private-key') 
  }
  
  stages {
    stage('RunPlaybook') {
      steps {
        sh 'ansible-playbook -i inventory/walmart.hosts --private-key=$AWSEC2_PRIVATE_KEY playbooks/installTomat.yml'
      }
    }
  
  }//stages closing
}//pipeline closing
