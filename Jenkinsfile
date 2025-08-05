pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://22E329344221EE784C6DB817AE38722C.gr7.eu-central-1.eks.amazonaws.com']]) {
                  sh "kubectl apply -f deployment-service.yml --watch"
                  sleep 60    
                }
            }
        }
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://22E329344221EE784C6DB817AE38722C.gr7.eu-central-1.eks.amazonaws.com']]) {
                sh "kubectl get all -n webapps"
                }
            }
       }
   }
}


