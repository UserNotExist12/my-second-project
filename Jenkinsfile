pipeline {
  agent any
  environment {
    a1 = 'a1111111'
    a2 = 'a2222222'
    a3 = "${env.JOB_NAME + env.BUILD_NUMBER + '/13211'}"
  }
  stages {
    stage('Stage 1') {
      parallel {
        stage('Parallel1-Stage 1') {
          environment {
            a1 = 'a1111111-stage1'
            a2 = 'a2222222-stage1'
            a3 = "${env.JOB_NAME + env.BUILD_NUMBER + '/13211-stage1'}"
          }
          steps {
            echo env.a2
            sh 'printenv'
            echo 'step1'
            sh 'sleep 20'
            sh 'echo "this is a script"'
            sh 'mkdir sub1'
            dir(path: 'sub1') {
              sh 'mkdir aaa && cd aaa && pwd'
            }

            sh 'pwd'
            sh 'aaaaa=1123'
            sh 'echo ${a3}'
            echo '${a3}'
            echo "${a3}"
          }
        }
        stage('Parallel1-Stage 2') {
          environment {
            paralell = 'true'
          }
          steps {
            sh 'pwd'
            sleep 20
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
        sh 'pwd'
        echo 'step1'
        echo 'step2'
        sh 'sleep 3s'
        sh 'echo "this is a script"'
        sh '''
          echo 1
          echo ${a2}
        '''
        sh """
          echo 1
          echo ${a2}
        """
      }
    }
    stage('Stage 3: in docker') {
      agent {
        docker { image 'busybox' }
      }
      environment {
        a3 = 'docker'
        IN_DOCKER = 'yes'
      }
      steps {
        checkout scm
        sh 'sleep 1m'
        sh 'ls -al /'
        sh 'export'
        sh 'printenv'
        sh 'ls -l'
        sh 'pwd'
      }
    }
  }
}
