pipeline {
  agent { 
  label 'ansible'
  }
  
  environment {
   AWS_EC2_PRIVATE_KEY=credentials('ec2-private-key') 
  }
  
  stages {
    
    //Get the Code from GitHub Repo git credentialsId: 'ec2privaye', url: 'https://github.com/priyankathammineni/jenkins-with-ansible.git'
    stage('CheckOutCode'){
      steps{
        git branch: 'master', credentialsId: 'aeeaa4ad-45b4-4c30-9401-586ac501a9bb', url: 'https://github.com/priyankathammineni/jenkins-with-ansible.git'
      }
    }
     
    //Run the playbook
    stage('RunPlaybook') {
      steps {
        sh "ansible-playbook -i inventory/walmart.hosts --private-key=$AWS_EC2_PRIVATE_KEY playbooks/installTomcat.yml --ssh-common-args='-o StrictHostKeyChecking=no'"
      }
    }
  
  }//stages closing
}//pipeline closing
