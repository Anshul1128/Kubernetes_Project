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
                    // this libne is very imp otherwise it will give error of private key issue.
                    sh 'ssh -o StrictHostKeyChecking=no -l ubuntu 13.126.18.139 uname -a'
                    sh "scp /var/lib/jenkins/workspace/K8s/Dockerfile ubuntu@13.126.18.139:/home/ubuntu"
                }       
            }
        }
//         stage('Docker Image Build') {
//             steps {
//                 sshagent(['ansible_demo']) {
//                     // this line is very imp otherwise it will give error of private key issue. Recommended for automates task only.
//                     sh 'ssh -o StrictHostKeyChecking=no -l ubuntu@65.2.39.69 uname -a'
//                     sh "scp /var/lib/jenkins/workspace/K8s/Dockerfile ubuntu@65.2.39.69:/home/ubuntu"
//                 }       
//             }
//         }


//     }
// }