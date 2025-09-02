pipeline {
    agent any

    environment {
        NAMESPACE = "koteswararao-namespace"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/gk020601/spring-boot.git'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh '''
                  echo "Deploying Spring Boot app to Kubernetes namespace: $NAMESPACE"

                  kubectl apply -f springboot-app-deployment.yaml -n $NAMESPACE
                  kubectl apply -f springboot-app-service.yaml -n $NAMESPACE

                  echo "Deployment completed."
                '''
            }
        }
    }
}


