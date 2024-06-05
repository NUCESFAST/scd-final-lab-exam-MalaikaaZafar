pipeline {
    agent any

     tools {
        nodejs 'NodeJSInstall'
        dockerTool 'dockerInstall'
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/NUCESFAST/scd-final-lab-exam-MalaikaaZafar'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

                stage('Build Docker Image') {
                    steps {
                        script {
                            bat 'docker-compose build'
                        }
                    }
                }
        
                // stage('Run Docker Image') {
                //     steps {
                //         script {
                //             bat 'docker run -p 3000:3000 my-image:%BUILD_ID%'
                //         }
                //     }
                // }
        
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