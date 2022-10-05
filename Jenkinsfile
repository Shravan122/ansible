pipeline {
    agent any    
    environment {
        ENV_URL       = "pipeline.google.com"
        SSH_CRED      = credentials('SSH')
    }

     stages { 
                        
         

          stage('Do a Dry-Run') {   // For Dry-run
           // when { branch pattern: "PR-.*", comparator: "REGEXP"}           // Runs only when it's a PR 
            steps {
                sh "env"
                sh "ansible-playbook  -e COMPONENT=mongodb -e dev-inv -e ansible_user=${SSH_CRED_USR} -e ansible_password=${SSH_CRED_PSW} robot-dryrun.yml"        
            }
        } 
     } 
}      