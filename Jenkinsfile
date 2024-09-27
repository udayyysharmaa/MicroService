pipeline {
    agent any

    stages {
        stage('Deploy to K8s') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://C2EB55E2B5939D80D93185D9772F4C09.gr7.ap-south-1.eks.amazonaws.com') {
                    sh 'kubectl apply -f deployment-service.yml'
                    sleep 60
                }
            }
        }
        stage('Verify to K8s') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://C2EB55E2B5939D80D93185D9772F4C09.gr7.ap-south-1.eks.amazonaws.com') {
                    sh 'kubectl get svc -n webapps'
                    
                }
            }
        }
    }
}
