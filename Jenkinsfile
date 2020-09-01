pipeline {
    agent any
    tools {
        maven 'M2_HOME'
    }   
        
          stages {
       
        stage('build') {
            steps {
                echo 'Hello build'
                sh 'mvn clean'
                sh 'mvn install'
                sh 'mvn package'
            }
        }
        
       stage('test') {
            steps {
                sh 'mvn test'
                
            }
        }
        stage ('build and publish image') {
     steps {  
      scripts { 
       checkout scm
       docker.WithRegistry('', 'dockerUserID') {   
       def customImage = docker.build("bertinlekane/holiday-pipeline:${env.BUILD_ID}")
       customImage.push()

    customImage.push('latest')
              
    }
}

