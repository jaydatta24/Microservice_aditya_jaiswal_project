pipeline {
    agent any

    stages {
        stage('Deploye to kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://CAF2DBD16F74FD40D683D0F3059AF250.gr7.ap-south-1.eks.amazonaws.com']]) {
                sh "kubectl apply -f deployment-service.yml"
           
                }
            }
        }
        
        stage('verify Deployement') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://CAF2DBD16F74FD40D683D0F3059AF250.gr7.ap-south-1.eks.amazonaws.com']]) {
                  sh "kubectl get svc -n webapps"
               }
            }
        }
    }
}
