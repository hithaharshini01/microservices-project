pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-01', contextName: '', credentialsId: 'k8s-secret', namespace: 'webapps', serverUrl: 'https://F9DCEAAFBB668DAE9CE438B102195C3A.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-01', contextName: '', credentialsId: 'k8s-secret', namespace: 'webapps', serverUrl: 'https://F9DCEAAFBB668DAE9CE438B102195C3A.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
