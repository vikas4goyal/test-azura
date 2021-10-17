pipeline {
  agent none
  stages {
    stage('Stage 1') {
      parallel {
        stage('Stage 1') {
          agent {
            docker {
              image 'vikas4goyal/aws-sam:0.0.1'
            }

          }
          steps {
            sleep 1
            script {
              sh 'ls'
              echo 'mytest'
            }

            sh 'mkdir -p build/YBAAuthorizer && touch build/YBAAuthorizer/myfile.txt'
            sh 'ls build/YBAAuthorizer'
            stash(name: 'stage-1', includes: 'build/**')
          }
        }

        stage('Stage 2') {
          agent {
            docker {
              image 'vikas4goyal/aws-sam:0.0.1'
            }

          }
          steps {
            sleep 1
            sh 'mkdir -p build/Login && touch build/Login/myfile.txt'
            stash(name: 'stage-2', includes: 'build/**')
          }
        }

        stage('Stage 3') {
          agent {
            docker {
              image 'vikas4goyal/aws-sam:0.0.1'
            }

          }
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
      agent {
        docker {
          image 'vikas4goyal/aws-sam:0.0.1'
        }

      }
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