pipeline{
    agent any

    environment {
        ANSIBLE_SERVER = '13.126.18.139'
        ANSIBLE_USER = 'ubuntu'
        // ANSIBLE_SSH_KEY = credentials('ansible_demo')
    }

    stages{
        stage("Cleanup Workspace"){
            steps {
                cleanWs()
            }

        }
    
        stage("Checkout from SCM"){
            steps {
                git branch: 'master', credentialsId: 'github', url: 'https://github.com/Anshul1128/Kubernetes_Project.git'
            }

        }
        stage('Copy File to Ansible Server') {
            steps {
                sshagent(['ansible_demo']) {
                    sh "scp ${WORKSPACE}/var/lib/jenkins/workspace/K8s/* ${ANSIBLE_USER}@${ANSIBLE_SERVER}:/home/ubuntu"
                }       
            }
        }

    }
}