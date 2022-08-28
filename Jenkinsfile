pipeline {
    agent any
    stages {
        stage('Build Docker image') {
            steps {
                sh 'sudo docker build -t my-prj-ui .'
                sh 'sudo docker tag my-prj-ui hardik794/my-prj-ui:v1'
            }
        }
        stage('Push Docker image') {
            environment {
                DOCKER_HUB_LOGIN = credentials('docker-hub')
            }
            steps {
                sh 'sudo docker login --username=$DOCKER_HUB_LOGIN_USR --password=$DOCKER_HUB_LOGIN_PSW'
                sh 'sudo docker push hardik794/my-prj-ui:v1'
            }
        }
    }
    post {
        // Clean after build
        always {
            cleanWs()
        }
    }
}
