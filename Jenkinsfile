pipeline {
  agent any
  stages {
    stage('Stage 1') {
      parallel {
        stage('Stage 1') {
          agent any
          environment {
            a1 = 'a1111111'
            a2 = 'a2222222'
            a3 = '${env.JOB_NAME}'
          }
          steps {
            echo env.a2
            sh 'printenv'
            echo 'step1'
            echo 'step2'
            sh 'sleep 5s'
            sh 'echo "this is a script"'
            sh 'mkdir sub1'
            dir(path: 'sub1') {
              sh 'mkdir aaa && cd aaa && pwd'
            }

            sh 'pwd'
            sh 'aaaaa=1123'
            sh 'echo ${aaaaa}'
          }
        }
        stage('Stage 1 Parallel') {
          agent any
          environment {
            paralell = 'true'
          }
          steps {
            sleep 4
            sh 'echo parallel'
          }
        }
      }
    }
    stage('Stage 2') {
      environment {
        a2 = '2'
      }
      steps {
        echo 'step1'
        echo 'step2'
        sh 'sleep 3s'
        sh 'echo "this is a script"'
        sh '''echo 1
echo 2'''
      }
    }
  }
}
