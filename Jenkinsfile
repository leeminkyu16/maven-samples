pipeline {
  agent any

  tools { 
      maven 'MY_MVN' 
      jdk 'MY_JDK'
  }

  parameters {
    string(name: "GIT_BISECT_START", defaultValue: "198644632661c67b6c32f59e9047c11a70685e15", description: "Starting commit for Git Bisect")
    string(name: "GIT_BISECT_END", defaultValue: "98ac319c0cff47b4d39a1a7b61b4e195cfa231e5", description: "Ending commit for Git Bisect")
  }


  stages {
    stage('Git: Checkout') {
      steps {
        git(url: 'https://github.com/leeminkyu16/maven-samples', branch: 'master')
      }
    }

    stage("Git: Bisect") {
      steps {
        sh "git bisect start ${params.GIT_BISECT_START} ${params.GIT_BISECT_END}"
        sh "git bisect run mvn clean test"
      }
    }
  }
}
