pipeline{
    agent any
    stages{
        stage('clone git repo'){
            steps{
                //Clone repo
                sh 'https://gitlab.com/qacdevops/chaperootodo_client.git'
            }
        }
        stage('install docker'){
            steps{
                //Install and give sudo rights to docker
                sh 'docker: curl https://get.docker.com | sudo bash'
                sh 'sudo usermod -aG docker $(whoami)'
                //Install docker-compose
                sh 'sudo apt update'
                sh 'sudo apt install -y curl jq'
                sh 'version=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | jq -r ".tag_name")'
                // download to /usr/local/bin/docker-compose
                sh 'sudo curl -L "https://github.com/docker/compose/releases/download/${version}/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose'
                sh 'sudo chmod +x /usr/local/bin/docker-compose'
            }    
        }
        stage('deploy'){
            steps{
                sh 'sudo docker-compose pull && sudo -E DB_PASSWORD=${DB_PASSWORD} docker-compose up -d'    
            }
        }
    }
}
