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
        sh 'ansible-playbook playbook.yaml -e \'ansible_python_interpreter=/usr/bin/python3\''
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