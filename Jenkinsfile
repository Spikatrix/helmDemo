pipeline {
    agent any

    environment {
        KUBECONFIG = credentials('kubeconfig')
    }

    stages {
        stage('Build') {
            steps {
                sh "helm dependency update ./exercise"
                sh "helm lint ./exercise"
                sh "helm package ./exercise"
            }
        }
        stage('Test') {
            steps {
                sh "helm upgrade mychart ./exercise --install --dry-run"
            }
        }
        stage('Deploy') {
            steps {
                sh "helm upgrade mychart ./exercise --install"
            }
        }
    }
}