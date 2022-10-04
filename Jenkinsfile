pipeline {
    agent any    
    environment {
        ENV_URL       = "pipeline.google.com"
        SSH_CRED      = credentials('SSH')
    }

     stages { 
         stage('Perform Lint Checks') {    // Runs only when it's a feature branch 
        when { branch pattern: "feature-.*", comparator: "REGEXP"} 
            steps {
                sh "env"
                sh "echo Performing Link Checks"           
            }
        } 

         stage('Do a Dry-Run') {  
           // when { branch pattern: "PR-.*", comparator: "REGEXP"}           // Runs only when it's a PR 
            steps {
                sh "env"
                sh "ansible-playbook  -e COMPONENT=mongodb -e dev-inv -e ansible_user=${SSH_CRED_USR} -e ansible_password=${SSH_CRED_PSW}"   robot-dryrun.yml        
            }
        } 
     } 
}      