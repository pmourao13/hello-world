pipeline {
  agent any
  tools {
    maven "Maven 3.8.6"
    jdk "JDK-11"
  }
  stages {
        stage('Initialize'){
            steps{
                echo "PATH = ${M2_HOME}/bin:${PATH}"
                echo "M2_HOME = /home/jenkins/"
            }
        }
        stage('Build') {
          // agent { label 'Centos7' }
            steps {
                dir("/opt/jenkins/agent/workspace/MavenPipeline/hello-world") {
                sh 'mvn -B -DskipTests clean package pom.xml'
                }
            }
        }
     }
    post {
       always {
          junit(
        allowEmptyResults: true,
        testResults: '*/test-reports/.xml'
      )
      }
   } 
}
