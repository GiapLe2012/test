pipeline {
    agent any
    environment {
        PROJECT_ID = 'PROJECT-ID'
        CLUSTER_NAME = 'kube1'
        LOCATION = 'CLUSTER-LOCATION'
        CREDENTIALS_ID = 'gke'
    }
    stages {
        stage("Checkout code") {
            steps {
                checkout scm
            }
        }
        stage("Build image") {
            steps {
                script {
                    sh "docker login -u giaple -p P@ssw0rd123456"
                    myapp = docker.build("giaple/demo:${env.BUILD_ID}")
                }
            }
        }
        stage("Push image") {
            steps {
                script {
                    sh "docker login -u giaple -p P@ssw0rd123456"
                    sh "docker push giaple/demo:${env.BUILD_ID}"
                       
                }
            }
        }        
        stage('Deploy to Kubenetes-Local') {
            steps{
                sh "sed -i 's/hello:latest/hello:${env.BUILD_ID}/g' deployment.yaml"
                sh "kubectl apply -f deployment.yaml"
            }
        }
    }    
}