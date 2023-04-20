pipeline {
  agent any
  tools {
    maven 'maven'
  }
  stages{
    stage('1-git-clone'){
      steps{
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-id', url: 'https://github.com/etechDevops/etech-mavenApp.git']]])
      }
    }
    stage('2-cleanws'){
      steps{
        sh 'mvn clean'
      }
    }
    stage('3-mavenbuild'){
      steps{
        sh 'mvn package'
      }
    }
    stage('unittest'){
        steps{
            sh 'mvn test'
        }
    }
    stage('codequality'){
        steps{
       sh 'mvn clean verify sonar:sonar \
  -Dsonar.projectKey=team5codereview \
  -Dsonar.projectName='team5codereview' \
  -Dsonar.host.url=http://ec2-3-87-32-180.compute-1.amazonaws.com:9000 \
  -Dsonar.token=sqp_9b06323fc4fcc8f028ae2515d68b9eb3f31b593bmvn clean verify sonar:sonar \
  -Dsonar.projectKey=team5codereview \
  -Dsonar.projectName='team5codereview' \
  -Dsonar.host.url=http://ec2-3-87-32-180.compute-1.amazonaws.com:9000 \
  -Dsonar.token=sqp_9b06323fc4fcc8f028ae2515d68b9eb3f31b593b'
        }
    }
  }
}
