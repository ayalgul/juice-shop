pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'I am in the build stage'
        git(url: 'https://github.com/ayalgul/juice-shop.git', branch: 'master')
      }
    }

    stage('Test') {
      steps {
        echo 'I am in the Test Stage '
      }
    }

    stage('Deploy') {
      steps {
        echo 'I am in the Deploy stage '
      }
    }

  }
}