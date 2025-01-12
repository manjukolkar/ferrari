pipeline{
    agent any

    tools {
        jdk 'java-11'
        maven 'maven'
    } 

    stages{
        stage('Git-Checkout'){
            steps{
                git branch: 'master', url: 'https://github.com/manjukolkar/web-application.git'
            }
        }
        stage('Compile'){
            steps{
                sh 'mvn compile'
            }
        }
        stage('Build'){
            steps{
                sh 'mvn package'
            }
        }
        stage('Build and tag'){
            steps{
                sh 'docker build -t manjukolkar007/cd:1 .'
            }
        }
        stage('Containerisation'){
            steps{
                sh '''
                docker run -it -d --name c1 -p 9001:8080 manjukolkar007/AB:1
                                 '''
            }
        }
        stage('Docker-login'){
            steps{
                 script {
                            withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                                sh "echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin"
                            }
                        }
            }
        }
        stage('pushing to docker repository'){
            steps{
                 sh 'docker push manjukolkar007/AB:1'
            }
        }
    }
}