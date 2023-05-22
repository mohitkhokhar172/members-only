pipeline{
  agent {label 'slave'}
    options {
       skipStagesAfterUnstable()
       }
    stages {
      stage('clone repo') {
        steps {
          script {
            checkout scm
            }
          }
        }
      stage('build') {
        steps {
          script {
            app =docker.build("underwater")
            }
          }
        } 
       stage('test'){
         steps {
           scho 'empty'
           }
         }
       stage('deploy') {
         steps {
           script {
             docker.withRegistry('877594857616.dkr.ecr.us-east-1.amazonaws.com/sample', 'ecr:us-east-1:aws-credentials'){
               app.push("${env.BUILD_NUMBER}")
             app.push("latest")
             }
           }
         }
       }
     }
   }  
