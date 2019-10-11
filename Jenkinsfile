pipeline {
     agent any
     stages {
          stage("Compile") {
               steps {
                    sh "/usr/bin/mvn compile"
               }
          }
          stage("Unit test") {
               steps {
                    sh "/usr/bin/mvn test"
               }
          }
     
    
stage("Package") {
     steps {
          sh "/usr/bin/mvn package"
     }
}
          
          stage('SonarQube Analysis') {
        def mvnHome =  tool name: 'maven-3', type: 'maven'
        withSonarQubeEnv('sonarqube') { 
          sh "usr/bin/mvn sonar:sonar"
        }
          
          stage("Docker build") {
     steps {
      
          sh "docker build -t pathik_tomcat ."
     }
}
          

stage("Deploy to staging") {
     steps {
 
          sh "docker run -d -it -v /var/lib/jenkins/workspace/DockerContainer/target/:/usr/local/tomcat/webapps/ -p 9090:8080 --name Testtomcat1 pathik_tomcat"
     }
}




     }
  post {
     always {
          sh "echo 'Successfull It'"
     }
}
}
