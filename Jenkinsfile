pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/NUCESFAST/scd-final-lab-exam-MalaikaaZafar'
            }
        }

        stage('Install Dependencies') {
            steps {
                   dir('./Auth') {
                    bat 'npm install'
                }
                    dir('./Post'){
                        bat 'npm install'
                    }
                    dir('./Classrooms'){
                        bat 'npm install'
                    }
                    dir('./event-bus'){
                        bat 'npm install'
                    }
                    dir('./client'){
                        bat 'npm install'
                    }
            }
        }

                stage('Build Docker Image') {
                    steps {
                        script {
                            bat 'docker-compose build'
                        }
                    }
                }
        
                stage('Push Docker Image') {
                    steps {
                        withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                            bat 'docker login -u %DOCKER_USER% -p %DOCKER_PASS% https://registry.hub.docker.com'
                            bat 'docker-compose push'
                        }
                    }
                }
            }
        }