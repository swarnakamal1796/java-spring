pipeline {
    agent any

    stages {
       
        stage('maven build ') {
            steps {
               sh 'mvn clean package'
            }
        }
        
        stage('docker image build ') {
            steps {
                sh 'docker build -t java-spring-19:v1 .'
            }
        }
        stage('docker login ') {
            steps {
                sh 'docker login '
            }
        }
        stage('docker tagging ') {
            steps {
                sh 'docker tag java-spring-19:v1 malleshdevops/devops19:spring-19.1'
            }
        }
      stage('image push ') {
            steps {
                sh 'docker push malleshdevops/devops19:spring-19.1'
            }
        }

    }
    post{
        always{
            emailext body: '''Hi,

     The jenkins has been failed . please check it.

     Thanks
     Devops Team''', subject: 'testing jenkins pipeline: $JOB_URL', to: 'malleshdevops2021@outlook.com'
    }
    }

}
