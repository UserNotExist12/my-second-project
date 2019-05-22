pipeline {
  agent any
  stages {
    stage('Stage 1') {
      agent any
      environment {
        a1 = '1'
      }
      steps {
        echo 'step1'
        echo 'step2'
        sh 'sleep 5s'
        sh 'echo "this is a script"'
      }
    }
    stage('Stage 2') {
      agent any
      environment {
        a2 = '2'
      }
      steps {
        echo 'step1'
        echo 'step2'
        sh 'sleep 3s'
        sh 'echo "this is a script"'
      }
    }
  }
}