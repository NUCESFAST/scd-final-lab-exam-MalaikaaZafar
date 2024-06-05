pipeline {
    agent any
    stages {
        stage('i211110Checkouti211110') {
            steps {
                git 'https://github.com/NUCESFAST/scd-final-lab-exam-MalaikaaZafar'
            }
        }

        stage('i211110 Install Dependencies i211110') {
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

                stage('i211110Build Docker Imagei211110') {
                    steps {
                        script {
                            bat 'docker-compose build'
                        }
                    }
                }
        
                stage('i211110Push Docker Imagei211110') {
                    steps {
                        withCredentials([usernamePassword(credentialsId: 'dfce01d0-1003-41f6-9e3c-965f103e5b23', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                            bat 'docker login -u %DOCKER_USER% -p %DOCKER_PASS% https://registry.hub.docker.com'
                            bat 'docker-compose push'
                        }
                    }
                }
            }
        }