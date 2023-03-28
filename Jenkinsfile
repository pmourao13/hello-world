pipeline {
  agent none
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
          agent { node { label 'darthAgent' } }
            steps {
                dir("/opt/jenkins/agent/workspace/MavenPipeline/hello-world") {
                sh 'mvn -B -DskipTests clean package'
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
