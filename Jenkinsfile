pipeline {
    agent { label 'slavenode' }

    stages {
        stage('Pull') {
            steps {
                script {
                    if (fileExists('To-Do-App')) {
                        dir('To-Do-App') {
                            sh 'git pull'
                        }
                    } else {
                        sh 'git clone https://github.com/josanchezva/To-Do-App.git'
                    }
                }
            }
        }
        stage('build'){
            steps{
                dir('To-Do-App'){
                    sh 'docker compose up --build -d'
                }
            }
        }
        stage('Test'){
            steps{
                dir('To-Do-App'){
                    sh 'docker exec app-container yarn test'
                }
            }
        }
    }
}
