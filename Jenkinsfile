pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-rajesh', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://56FCA03495E910F7017EA667FE3682C0.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-rajesh', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://56FCA03495E910F7017EA667FE3682C0.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
