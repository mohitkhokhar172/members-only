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
            sh 'whoami'
            app =docker.build("underwater")
            }
          }
        } 
       stage('test'){
         steps {
           echo 'empty'
           }
         }
       stage('deploy') {
         steps {
           script {
              sh 'rm  ~/.dockercfg || true'
              sh 'rm ~/.docker/config.json || true'
             docker.withRegistry('877594857616.dkr.ecr.us-east-1.amazonaws.com/sample', 'aws_credentials'){
               app.push("${env.BUILD_NUMBER}")
             app.push("latest")
             }
           }
         }
       }
     }
   }  
