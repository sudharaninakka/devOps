pipeline {
    agent any
    stages {
        stage('Checkout Git') {
            stage('Checkout Git') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/Rajesh3284/devOps.git']]])
            }
        }
        stage('Build image') {
            steps {
                // Build the Docker image using the Dockerfile in the repo
                sh 'docker build -t mysite .'
            }
        }
        stage('Push image to Docker Hub') {
            steps {
                // Push the Docker image to Docker Hub repository
                sh 'docker push sriharsha7/devops:mysite'
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                // Deploy the Docker image to Kubernetes using kubectl
                sh 'kubectl apply -f kubernetes-manifest.yaml'
            }
        }
    }
}
