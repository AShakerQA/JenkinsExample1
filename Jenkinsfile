pipeline{
    agent any
    stages{
        stage('make python script'){
            steps{
            //Create the file
            sh "chmod +x ./example.sh"
            sh "./example.sh"
            }
        }
        stage('run python script'){
            steps{
            //Run script with python3
            sh 'python3 helloworld.py'
            }    
        }
   }
   }
