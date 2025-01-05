pipeline {
    agent {
        label 'Node-1'
    }

    stages {
        stage('Host Name') {
            steps {
                sh 'hostname'
            }
        }
        stage('Server IP address') {
            steps {
                sh 'hostname -I'
            }
        }
        stage('Ram Usage') {
            steps {
                sh 'free -gh'
            }
        }
        stage('Disk Usage') {
            steps {
                sh 'df -kh'
            }
        }
        stage('Process Running') {
            steps {
                sh 'ps -eaf'
            }
        }
        stage('CPU Utilization') {
            steps {
                sh 'lscpu'
            }
        }
    }
}
