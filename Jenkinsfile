pipeline {
    agent {
        label 'Windows'
    }
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('build') {
      steps {
        sh "mvn test"
      }
    }
    stage('archive') {
      steps {
        archive 'target/*.jar'
      }
    }
  }
  post {
      always{
        junit '**/target/surefire-reports/TEST-*.xml'
      }
    }
  }
}
