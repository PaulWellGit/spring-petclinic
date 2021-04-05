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
            sh 'mvn sonar:sonar -Dsonar.login=4875c0cce292b560bbde45d0000338cfd71f332a -Dsonar.host.url=http://localhost:9000'
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

    stage('Deploy') {
      steps {
        sh 'java -jar *.jar'
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