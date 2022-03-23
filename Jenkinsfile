pipeline {
  agent {
    node {
      label 'slave 1'
    }

  }
  stages {
    stage('Build') {
      steps {
        bat 'mvn -B -DskipTests clean package'
      }
    }

    stage('Test') {
      post {
        always {
          junit 'target/surefire-reports/*.xml'
        }

      }
      steps {
        echo 'Hello !! this is version 1.0'
      }
    }

  }
}