pipeline {
    agent any

    environment {
        imagename = "ehgur1104/canary"
        registryCredential = 'dockerhub'
        dockerImage = ''
    	  }
        stage('Bulid Docker') {
          agent any
          steps {
            echo 'Bulid Docker'
            script {
                dockerImage = docker.build imagename
            }
          }
          post {
            failure {
              error 'This pipeline stops here...'
            }
          }
        }
        // docker push
        stage('Push Docker') {
          agent any
          steps {
            echo 'Push Docker'
            script {
                    docker.withRegistry( '', registryCredential) {
                    dockerImage.push("1.0")  // ex) "1.0"
            }
          }
        }
          post {
            failure {
              error 'This pipeline stops here...'
            }
          }
        }
      } 

