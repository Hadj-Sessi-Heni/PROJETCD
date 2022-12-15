pipeline
{
   agent any
   
    stages {
        
 stage(' GIT ') {
            steps {
                echo 'Pulliing ...';
                git branch: 'master', url: 'https://github.com/Hadj-Sessi-Heni/PROJETCD.git'          
            }
     
        }
        stage(' install node modules ') {
            steps {
            sh ' npm install' 
            
            }
        }
         stage('build')
         {
             steps{
                 script{
                     sh "ansible-playbook Ansible/build.yml -i Ansible/inventory/host.yml -e ansible_become_password=0"
                 }
             }
         }
         
         stage('docker'){
            steps{
                script{
                    sh "ansible-playbook Ansible/docker.yml -i Ansible/inventory/host.yml -e ansible_become_password=0"
                }
            }
        }
        
         stage('docker-registry'){
            steps{
                script{
                    sh "ansible-playbook Ansible/docker-registry.yml -i Ansible/inventory/host.yml -e ansible_become_password=0"
                }
            }
        }
        
         
         }
         
         
}
