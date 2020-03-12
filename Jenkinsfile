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
                sh 'helm search nginx'
                sh 'helm install nginx' 
            }
        }
        stage('Deploy') {
            steps {
                sh 'make publish'
            }
        }
    }
}