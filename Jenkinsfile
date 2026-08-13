pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-cred', namespace: 'webapp', serverUrl: 'https://06D8EEF35E1E75A4651E1C52E5BE8137.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-cred', namespace: 'webapp', serverUrl: 'https://06D8EEF35E1E75A4651E1C52E5BE8137.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapp"
                }
            }
        }
    }
}
