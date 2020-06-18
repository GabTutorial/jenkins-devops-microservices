pipeline {
      agent any
      //agent { docker { image 'node:13.8'} }
      environment {
        dockerHOME = tool 'myDocker'
        mavenHome = tool 'myMaven'
        PATH = "$mavenHome/bin:$dockerHome/bin:$PATH"
      }
      stages {	
         stage ('Checkoout'){
            steps {
              echo "mavenHome $mavenHome"
              echo "$PATH"
              sh 'docker version'
              sh 'mvn --version'
              echo "Build"
              echo " $PATH $env.BUILD_NUMBER $env.BUILD_ID $env.JOB_NAME "
            }
         }
         stage('Compile'){
           steps {
               sh 'mvn clean compile'
           }
         }
         stage ('Test'){
       	    steps {
       	       sh 'mvn test'
       	    }
       	 }
         stage ('Integration test'){
       	    steps {
       	      sh 'mvn failsafe:integration-test failsafe:verify'
       	    }
         }
         stage ('Package'){
            steps {
              sh 'mvn package -DskipTest'
            }

       	 }
         stage ('Build Docker Image'){
            steps {
              //"docker build -t gabdock78/currency-exchange-devops:$env.BUILD_TAG"
              script {
                dockerImage=docker.build("gabdock78/currency-exchange-devops:${env.BUILD_TAG}")
              }
            }
         }
          stage ('Push Docker Image'){
             steps {
               script{
                docker.withRegistry('','dockerhub') {
                  dockerImage.push();
                  dockerImage.push('latest');
                }  
               }
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
