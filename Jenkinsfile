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
                    // This line is very important, else it will give error of 'private key' issue.
                    sh 'ssh -o StrictHostKeyChecking=no -l ubuntu 35.154.152.92 uname -a'
                    sh "scp /var/lib/jenkins/workspace/K8s/Dockerfile ubuntu@35.154.152.92:/home/ubuntu"
                }       
            }
        }
        stage('Docker Image Build') {
            steps {
                sshagent(['ansible_demo']) {
                    // this line is very imp otherwise it will give error of private key issue. Recommended for automates task only.
                    sh 'ssh -o StrictHostKeyChecking=no -l ubuntu 35.154.152.92 cd /home/ubuntu/'
                    sh 'ssh -o StrictHostKeyChecking=no -l ubuntu 35.154.152.92 docker image build -t $JOB_NAME:v1.$BUILD_ID .'
                }       
            }
        }


    }
}