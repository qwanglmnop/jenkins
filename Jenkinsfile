pipeline {
  agent any
  stages {
    stage('pre script') {
      parallel {
        stage('pre script') {
          steps {
            echo 'Hello world'
          }
        }

        stage('') {
          steps {
            sh 'echo "ni hao"'
          }
        }

      }
    }

    stage('post script') {
      steps {
        sh 'bye bye world'
      }
    }

  }
}
