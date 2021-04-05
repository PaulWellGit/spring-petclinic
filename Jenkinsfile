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

    stage('Testing') {
      parallel {
        stage('Testing') {
          steps {
            sh 'mvn sonar:sonar -Dsonar.login=6e61857779d1605c4df246b85f57385c558c3529 -Dsonar.host.url=http://localhost:9000'
          }
        }

        stage('SonarQube Test') {
          steps {
            echo "The tester is ${TESTER}"
            sleep 10
          }
        }

        stage('Print build number') {
          steps {
            echo "This is build number ${BUILD_ID}"
            sleep 20
          }
        }

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