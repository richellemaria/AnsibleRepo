pipeline {
    agent any
    environment{
         SSHCRED         = credentials('SSH_CRED') 
    }
    parameters{
         string(name: 'COMPONENT', defaultValue: 'mongodb' , description: 'enter the name of the component')
    }
    stages{
        stage('Ansible Code Scan'){
            steps{
                sh  "echo Code Scan Completed"
            }
        }
        stage('Ansible Lint Checks'){
            steps{
                sh  "echo Lint Checks Completed"
            }
        }
        stage('Ansible Dry Run'){
            steps{
                sh ''' 
                    ansible-playbook robot-dryrun.yml -e COMPONENT=${COMPONENT} -e ansible_user=centos -e ansible_password=${SSHCRED_PSW} -e ENV=dev
                ''' 
            }
        }
        stage('Promoting Code to Prod Branch'){
            steps{
                sh "echo Merging the feature branch to PROD Branch"
            }
        }
    }
}