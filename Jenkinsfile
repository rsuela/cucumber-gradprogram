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
        bat "gradlew test --rerun-tasks --info"
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
      junit '**/build/test-results/test/TEST-*.xml'
      cucumber fileIncludePattern: '**/Cucumber.json', sortingMethod: 'ALPHABETICAL'
    }
  }
}
