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
     }
}