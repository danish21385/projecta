pipeline {
    agent any
    
    environment {
      tag = "${env.BUILD_NUMBER}"
    }
    
    stages {
        stage('Checkout Source') {
            steps {
                git 'https://github.com/danish21385/projecta.git'
            }
        }
        stage('Docker Build') {
            steps {
                sh 'docker build -t danahmed/project1:${tag} . '
            }
        }
        stage('Docker Push') {
            steps {
                sh 'docker push danahmed/project1:${tag} '
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                script {
                    sh 'helm upgrade --install project1 myapp/. --set=image.tag=${tag} '
                }
            }
        }
    }
}
