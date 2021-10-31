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
                sh 'docker run --rm -d -p 8046:8080 --name springbootr --link mysqldbq:mysql springbootq'
             }
         }
     }
}
