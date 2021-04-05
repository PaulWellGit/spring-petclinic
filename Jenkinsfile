pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Start Build'
        sh 'mvn clean install -Dlicense.skip=true'
        echo 'Build Complete'
      }
    }

    stage('Testing') {
      parallel {
        stage('Testing') {
          steps {
            sh 'mvn sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dlicense.skip=true'
          }
        }

        stage('SonarQube Test') {
          steps {
            echo 'The tester is ${TESTER}'
            sleep 10
          }
        }

        stage('Print build number') {
          steps {
            echo 'This is build number ${BUILD_ID}'
            sleep 20
          }
        }

      }
    }

  }
  tools {
    maven 'maven'
  }
}