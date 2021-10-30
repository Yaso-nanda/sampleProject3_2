pipeline {
     agent any
     
     stages {
         stage('Build') {
            steps {
                sh 'mvn install -DskipTests'
            }
         }
         stage('Deploye'){
             steps {
                sh 'docker build -t springbootq:$BUILD_NUMBER .'
                sh 'docker run -d -p 8045:8080 --name springbootq --link mysqldbp:mysql springbootq:$BUILD_NUMBER'
                sh 'docker rmi springbootq:$BUILD_NUMBER'
                sh 'docker rmi springboot1:latest'
             }
         }
     }
}
