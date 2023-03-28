pipeline {
  agent darthAgent
  tools {
    maven "Maven 3.8.6"
  }
  
  stages {
    stage ('Build Artifact') {
      steps {
        sh "mvn clean package -DskipTests=true"
        archive 'target/*.war'
      }
    }
