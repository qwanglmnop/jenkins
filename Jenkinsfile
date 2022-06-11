pipeline {
  agent any
  stages {
    stage('pre script') {
      parallel {
        stage('step 1') {
          steps {
            sh 'echo "Hello world"'
          }
        }

        stage('parallel to step 1') {
          steps {
            sh 'echo "Parallel Hello"'
          }
        }

      }
    }

    stage('post script') {
      steps {
        sh 'echo "bye bye world"'
      }
    }

  }
}
