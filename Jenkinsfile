pipeline {
     agent any
     
     stages {
         stage('Build') {
            steps {
                sh 'mvn clean install -DskipTests'
            }
         }
         stage('Deploy'){
             steps {
                sh 'docker build -t springbootq .'
                sh 'docker run -d -p 8045:8080 --name springbootq --link mysqldbq:mysql springbootq'
             }
         }
     }
}
