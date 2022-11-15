pipeline {
    agent any
    stages {
        stage ("Pull") {
            steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/main']],
                    userRemoteConfigs: [[
                        url: 'https://github.com/im-playmaker/projetCD.git']]])
                }
            }
        }
   stage('python test'){
            steps{
                script{
                    sh "python3 --version"
                }
            }
        }
        stage('Build'){
            steps{
                script{
                    sh "ANSIBLE_DEBUG=1 ansible-playbook ansible/build.yml -i ansible/inventory/host.yml"
                }
            }
        }
		 stage('docker'){
            steps{
                script{
                    sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml"
                }
            }
        }
       
    }
}
