pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Start Build'
        sh 'mvn clean install'
        echo 'Build Complete'
      }
    }

    stage('Deploy') {
      steps {
        sh 'ansible-playbook playbook.yaml'
      }
    }

  }
  tools {
    maven 'maven'
  }
  environment {
    TESTER = 'Paul'
    BUILD_ID = '1'
  }
}