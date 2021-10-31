pipeline {
     agent any
     
     stages {
         stage('Build') {
            steps {
                sh 'mvn install -DskipTests'
            }
         }
         stage('Deploy'){
             steps {
                sh 'docker build -t springbootq .'
                sh 'docker run -d -p 8045:8080 --name springbootq --link mysqldbp:mysql springbootq'
             }
         }
     }
}
