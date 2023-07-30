pipeline {
     agent any

     stages {
          stage('Build Image'){
               steps {
                    script {
                         dockerapp = docker.build("ediplo/green", '-f ./GreenHomeImage/Dockerfile ./GreenHomeImage')
                    }
               }

          }
     }
}