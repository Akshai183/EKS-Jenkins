pipeline {
   agent any
   environment {
      PROJECT = 'WELCOME TO K8S B23 BATCH - Jenkins Class'
   }
   stages {
      stage('Check The Kubernetes Access') {
         steps {
            su jenkins -c 'aws eks --region us-east-2 update-kubeconfig --name eks-cluster-01'
            sh 'kubectl get pods -A'
            sh 'kubectl get ns'
         }
      }
      stage('Deploy Voting App') {
         steps {
            
            sh 'ls'
            sh 'kubectl apply -f voting-with-ingress.yml'
            sh 'kubectl apply -f ingress.yml'
            sh 'kubectl apply -f ingress-nk.yml'
            sh 'kubectl get pods,svc,ingress'
         }
      }
      stage('Deploy Ingress for Vote & Result') {
         steps {
            
            sh 'kubectl apply -f ingress.yml'
            sh 'kubectl get ingress'
         }
      }
      stage('Validating Deployment') {
         steps {
            
            sh 'kubectl get pods,deployment,svc'
         }
      }
   }
}
