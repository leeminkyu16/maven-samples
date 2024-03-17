pipeline {
  agent any

  tools { 
      maven 'MY_MVN' 
      jdk 'MY_JDK'
  }


  stages {
    stage('Git: Checkout') {
      steps {
        git(url: 'https://github.com/leeminkyu16/maven-samples', branch: 'master')
      }
    }

    stage('Maven: Test') {
      steps {
        sh 'mvn test'
      }
    }

    stage('Maven: Verify') {
      steps {
        sh 'mvn verify'
      }
    }

    stage('Maven: Clean') {
      steps {
        sh 'mvn clean'
      }
    }
  }
}