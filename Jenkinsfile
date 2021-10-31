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
                sh 'docker run --rm -d -p 8050:8080 --name springbootb --link mysqldbq:mysql springbootq'
             }
         }
     }
}
