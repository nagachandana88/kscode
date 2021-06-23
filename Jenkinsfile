pipeline {
  agent {label 'CI-pipeline'}
   //agent any
    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "Maven-3.6.3"      
    }
  stages {
     stage('git clone') {
      steps {
       git credentialsId: 'github', url: 'https://github.com/nagachandana88/kscode.git'
                  }
     }
    stage('Build clean') {
        steps {
         sh 'mvn clean'
        }
    }
 stage('Build compile') {
     steps {
         sh 'mvn compile'
        }
    }
  stage('sonarqube codescan'){
     steps{
            sh'mvn sonar:sonar \
            -Dsonar.projectKey=chandana \
            -Dsonar.host.url=http://18.117.136.142:9000 \
            -Dsonar.login=718c6ffec39069d6d68b5a75a80e5081c618db43'
          }
   }
 stage('Build test') {
       steps {
           sh 'mvn test'
        }
    }
 stage('Build package') {
        steps {
         sh 'mvn package'
        }
    }
 stage('Build deploy') {
       steps{
           sh 'mvn deploy'
        }
    }
 }
}
