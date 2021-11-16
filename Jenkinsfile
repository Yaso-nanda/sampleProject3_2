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
                sh 'docker rm -f springboota || true'
                sh 'docker run -d -p 8050:8080 --name springboota --link mysqldbq:mysql springbootq'
             }
         }
     }
}
