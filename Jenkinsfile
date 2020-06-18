pipeline {
      agent any
      stages {	
         stage ('Build'){
            steps {
              echo "Build"
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
      } post {
          always {
            echo "Im the fucking amo"
          }
          success {
            echo "I run when is OK"
          }
          failure {
            echo "I run when is KO"
          }
      }
 }
