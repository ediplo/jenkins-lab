pipeline {
     agent any

     stages {
          stage('Build Image'){
               steps {
                    script {
                         dockerapp = docker.build("ediplo/green:${env.BUILD_ID}", '-f ./GreenHomeImage/Dockerfile ./GreenHomeImage')
                    }
               }

          }

           stage('Push Image'){
               steps {
                    script {
                         docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                             dockerapp.push('latest')
                             dockerapp.push("${env.BUILD_ID}")
                         }
                    }
               }

          }

           stage('Deploy K8S'){
               steps {
                    withKubeConfig([credentialId: 'kubeconfig']) {
                         sh 'kubectl apply -f ./Kubernetes/green-deploy.yaml'
                    }
               }

          }
     }
}