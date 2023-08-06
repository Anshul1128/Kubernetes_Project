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
                sh "scp -i ansible_demo ${WORKSPACE}/var/lib/jenkins/workspace/K8s/* ubuntu@13.126.18.139:/home/ubuntu"
            }
        }

    }
}
        


// pipeline {
//     agent any
    
//     environment {
//         ANSIBLE_SERVER = ''
//         ANSIBLE_USER = 'ubuntu'
//         ANSIBLE_SSH_KEY = credentials('ansible')
//     }
    
//     stages{    
//         stage('GitCheckout') {
//             git 'https://github.com/Anshul1128/Kubernetes_Project.git'
//         }
        
        
//         stage('Copy File to Ansible Server') {
//             steps {
                // sh "scp -i 13.126.18.139 ${WORKSPACE}/var/lib/jenkins/workspace/K8s/* ubuntu@$13.126.18.139:/home/ubuntu"
//             }
//         }
//     }
// }







// node {

//     stage('GitCheckout') {
//             git 'https://github.com/Anshul1128/Kubernetes_Project.git'
//     }

//     stage('Sending Dockerfile to Ansible server over SSh') {
//       sshagent(['ansible']) {
//         //   steps {
//                 sh 'ssh -o StrictHostKeyChecking=no ubuntu@13.126.18.139'
//                 sh 'scp /var/lib/jenkins/workspace/K8s/* ubuntu@13.126.18.139:/home/ubuntu'
//                 sh "scp -i $ANSIBLE_SSH_KEY ${WORKSPACE}/path/to/your/file ${ANSIBLE_USER}@${ANSIBLE_SERVER}:/path/on/ansible/server"
//             // }
//         }
//     }
// }









