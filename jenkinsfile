pipeline {
    agent {
        label 'dev'  // Specify the label for the entire pipeline
    }
    
    stages {
        stage('clone project') {
            steps {
                dir('/home/kesari/Videos/') {
                    sh "rm -rf online-exam-portal online-exam-portal@tmp"
                    sh "git clone https://github.com/amit-hajare/online-exam-portal.git"
                }
            }
        }
       
        stage('build dockerfile frontend') {
            steps {
                dir('/home/kesari/Videos/online-exam-portal/frontend') {
                    sh "docker build -t frontend4 ."
                }
            }
        }
        
       
        stage('docker-compose up') {
            steps {
                dir('/home/kesari/Videos/online-exam-portal/') {
                    sh "docker compose up -d"
                }
            }
        }
    }
}



