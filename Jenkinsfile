pipeline {
     agent any
     
     stages {
         stage('SonarQube analysis & Mvn') {
              steps{
                   script{
                      scannerHome=tool 'sonarqube'
                   }
                   withSonarQubeEnv('sonarqube'){
                     sh "mvn clean install -DskipTests sonar:sonar \
                    -Dsonar.projectKey=sonar-maven \
                    -Dsonar.host.url=http://192.168.50.104:9000 \
                    -Dsonar.login=d33c224155aa7f3777856387ded0dccd7205a02b \
                    -Dsonar.sources=src/main/java/ \
                    -Dsonar.java.binaries=target/classes"
                   }
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
