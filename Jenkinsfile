pipeline { 
    agent any 
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') { 
            steps { 
                sh 'kubectl get nodes' 
            }
        }
        stage('Test'){
            steps {
                sh 'helm search repo nginx'
                sh 'helm install stable/nginx-ingress' 
            }
        }
        stage('Deploy') {
            steps {
                sh 'make publish'
            }
        }
    }
}