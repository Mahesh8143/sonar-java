pipeline {
    agent any
    
    stages{
        stage("CheckOut") {
            steps{
              checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Mahesh8143/sonar-java.git']]])
            }
        }
        stage('Test') {
            steps {
                sh 'mvn --version'
            }
        }
        stage("Maven Build") {
            steps {
                sh 'mvn clean install -f my-app/pom.xml'
            }
        }
         stage('Deploy') {
            when {
              expression {
                currentBuild.result == null || currentBuild.result == 'SUCCESS'
              }
            }
            steps {
               echo "successfully depoyed"
            }
        } 
    }
}
