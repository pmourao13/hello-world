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
    stage ('clone repo') {
      steps {
        dir("/opt/jenkins/agent/workspace/MavenPipeline/hello-world")
        sh 'git clone -b master https://github.com/pmourao13/hello-world.git'
      }
    }
    
        stage('Build') {
          // agent { label 'Centos7' }
            steps {
                dir("/opt/jenkins/agent/workspace/MavenPipeline/hello-world") {
                sh 'mv /opt/jenkins/agent/workspace/MavenPipeline/hello-world/hello-world/* /opt/jenkins/agent/workspace/MavenPipeline/hello-world/ && rm -rf /opt/jenkins/agent/workspace/MavenPipeline/hello-world/hello-world/'
                sh 'ls -lh /opt/jenkins/agent/workspace/MavenPipeline/hello-world/'
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
