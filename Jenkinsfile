pipeline {
  agent {
    docker {
      image 'vikas4goyal/aws-sam:0.0.1'
      args '-v /var/run/docker.sock:/var/run/docker.sock'
    }

  }
  stages {
    stage('Stage 1') {
      parallel {
        stage('Stage 1') {
          agent any
          steps {
            sleep 1
            sh 'mkdir -p build/YBAAuthorizer && touch build/YBAAuthorizer/myfile.txt'
            sh 'ls build/YBAAuthorizer'
            stash(name: 'stage-1', includes: 'build/**')
            script {
              sh 'ls'
              echo 'mytest'
            }

          }
        }

        stage('Stage 2') {
          agent any
          steps {
            sleep 1
            sh 'mkdir -p build/Login && touch build/Login/myfile.txt'
            stash(name: 'stage-2', includes: 'build/**')
          }
        }

        stage('Stage 3') {
          agent any
          steps {
            sleep 1
            echo 'I am Awake'
            sh 'mkdir -p build/Register && touch build/Register/myfile.txt'
            stash(name: 'stage-3', includes: 'build/**')
          }
        }

      }
    }

    stage('After') {
      agent any
      steps {
        echo 'All Step Done'
        unstash 'stage-1'
        unstash 'stage-2'
        unstash 'stage-3'
        sh 'ls build'
        sh 'pwd build/Login'
      }
    }

  }
}