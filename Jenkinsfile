pipeline {
    agent {
        label 'dev'  // Specify the label for the entire pipeline up to date no updated
    }
    
    stages {
        stage('clone project') {
            steps {
                dir('/home/kesari/workspace/sample-project') {
                    sh "rm -rf online-exam-portal online-exam-portal@tmp"
                    sh "git clone https://github.com/amit-hajare/online-exam-portal.git"
                }
            }
        }

        stage('docker container down') {
            steps {
                dir('/home/kesari/workspace/sample-project/online-exam-portal/frontend') {
                    sh "docker compose down"
                }
            }
        }

        stage('docker images delete') {
            steps {
                dir('/home/kesari/workspace/sample-project/online-exam-portal/frontend') {
                    sh "docker system prune -af"
                }
            }
        }
       
        stage('build dockerfile frontend') {
            steps {
                dir('/home/kesari/workspace/sample-project/online-exam-portal/frontend') {
                    sh "docker build -t frontend4 ."
                }
            }
        }
        
        stage('docker-compose up') {
            steps {
                dir('/home/kesari/workspace/sample-project/online-exam-portal/') {
                    sh "docker compose up -d"
                }
            }
        }
    }
}
