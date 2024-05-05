pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://BBE7963AA74C83CAEAF5336C7ACA68ED.gr7.us-east-1.eks.amazonaws.com']]) {
                sh "kubectl apply -f deployment-service.yml"
                sleep 60
}
            }
        }
         stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://BBE7963AA74C83CAEAF5336C7ACA68ED.gr7.us-east-1.eks.amazonaws.com']]) {
                sh "kubectl get svc -n webapps"
}
            }
        }
    }
}
