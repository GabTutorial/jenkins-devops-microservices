pipeline {
      agent any
      //agent { docker { image 'node:13.8'} }
      stages {	
         stage ('Build'){
            steps {
              // sh 'node --version'
              echo "Build"
              echo " $PATH $env.BUILD_NUMBER $env.BUILD_ID $env.JOB_NAME "
            }
         }
         stage ('Test'){
       	    steps {
       	      echo "Test"
       	    }
       	 }
         stage ('Integration'){
       	    steps {
       	      echo "Integration"
       	    }
       	 }
      } 

      post {
          always {
            echo 'Im the fucking amo'
          }
          success {
            echo 'I run when is OK'
          }
          failure {
            echo 'I run when is KO'
          }
      }
 }
