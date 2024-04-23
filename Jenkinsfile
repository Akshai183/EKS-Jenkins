pipeline {
   agent any
   environment {
      PROJECT = 'WELCOME TO K8S B23 BATCH - Jenkins Class'
      JENKINS_USERNAME = 'jenkins'
      JENKINS_PASSWORD = 'admin'
   }
   stages {
      stage('Check The Kubernetes Access') {
         steps {
                sh "su $JENKINS_USERNAME -c 'kubectl get pods -A'"
                sh "su $JENKINS_USERNAME -c 'kubectl get ns'"
         }
      }
      stage('Deploy Voting App') {
         steps {
            sh "su $JENKINS_USERNAME -c  'kubectl apply -f voting-with-ingress.yml'"
            sh "su $JENKINS_USERNAME -c  'kubectl apply -f ingress.yml'"
            sh "su $JENKINS_USERNAME -c  'kubectl apply -f ingress-nk.yml'"
            sh "su $JENKINS_USERNAME -c  'kubectl get pods,svc,ingress'"
         }
      }
      stage('Deploy Ingress for Vote & Result') {
         steps {
            
            sh "su $JENKINS_USERNAME -c  'kubectl apply -f ingress.yml'"
            sh "su $JENKINS_USERNAME -c  'kubectl get ingress'"
         }
      }
      stage('Validating Deployment') {
         steps {
            
            sh "su $JENKINS_USERNAME -c 'kubectl get pods,deployment,svc'"
         }
      }
   }
}
