pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'I am in the build stage'
        git(url: 'https://github.com/ayalgul/juice-shop.git', branch: 'master')
      }
    }

    stage('Build') {
      steps {
        echo 'I am in the Build Stage '
      }
    }

    stage('Test') {
      steps {
        echo 'I am in the Test stage '
      }
    }

  }
}