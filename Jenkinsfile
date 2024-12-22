pipeline {
    agent any
    environment {
        KUBECONFIG = credentials('k8s-config') // Configure credentials in Jenkins
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/your-username/k8s-jenkins-pipeline.git'
            }
        }
        stage('Deploy Kubernetes Objects') {
            steps {
                sh '''
                kubectl apply -f deployment.yaml
                kubectl apply -f service.yaml
                '''
            }
        }
        stage('Test Deployment') {
            steps {
                sh '''
                kubectl get pods
                kubectl get svc hello-app-service
                '''
            }
        }
    }
}
