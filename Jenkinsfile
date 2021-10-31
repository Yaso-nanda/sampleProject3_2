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
                sh 'docker stop springbootb'
                sh 'docker rm springbootb'
                sh 'docker run -d -p 8050:8080 --name springbootb --link mysqldbq:mysql springbootq'
             }
         }
     }
}
