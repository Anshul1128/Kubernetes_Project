pipeline{
    agent any


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
                    sh 'ssh -o StrictHostKeyChecking=no -l ubuntu@13.126.18.139'
                    sh "scp /var/lib/jenkins/workspace/K8s/* ubuntu@13.126.18.139:/home/ubuntu"
                }       
            }
        }

    }
}