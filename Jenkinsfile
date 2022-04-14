pipeline {
    agent any

    environment {
        KUBECONFIG = credentials('kubeconfig')
    }

    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                // git '<url>.git'

                sh "helm dependency update ./exercise"
                sh "helm list ./exercise"
                sh "helm package ./exercise"
                sh "helm install mychart ./exercise"
            }

            /* post {
                success {
                }
            } */
        }
    }
}