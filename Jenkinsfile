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
                sh "scp ${WORKSPACE}/var/lib/jenkins/workspace/K8s/* ${ANSIBLE_USER}@${ANSIBLE_SERVER}:/home/ubuntu"
                       
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


// pipeline {
//     agent any
//     stages {
//         stage('Copy File to Ansible Server') {
//             steps {
//                 script {
//                     // Replace these variables with your actual values
//                     def ansibleServer = 'ansible-server-ip'
//                     def ansibleUser = 'ansible-user'
//                     def sourceFile = 'path/to/source/file.txt'
//                     def destinationDir = 'path/to/destination/'

//                     // Execute the SCP command to copy the file to the Ansible server
//                     sh "scp -o StrictHostKeyChecking=no ${sourceFile} ${ansibleUser}@${ansibleServer}:${destinationDir}"
//                 }
//             }
//         }
//     }
// }







