pipeline {
      agent any
      stages {
         stage ('Build') {
          steps {
             sh '''cd $WORKSPACE
                   docker build -t devops:v${BUILD_NUMBER} .'''
             }
           }
           stage('push ECR'){
            steps {
                sh '''aws ecr get-login-password --region us-west-2 | docker login --username AWS --password-stdin 897276212041.dkr.ecr.us-west-2.amazonaws.com
           		    
			                 docker tag devops:v${BUILD_NUMBER} 897276212041.dkr.ecr.us-west-2.amazonaws.com/devops18-java:v${BUILD_NUMBER}
                    	 docker push 897276212041.dkr.ecr.us-west-2.amazonaws.com/devops18-java:v${BUILD_NUMBER}
		   
       '''
            }
          }
          }
        }
