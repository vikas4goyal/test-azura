pipeline {
  agent none
  stages {
    stage('Stage 1') {
      parallel {
        stage('Stage 1') {
          agent {
            docker {
              args '-v /var/run/docker.sock:/var/run/docker.sock'
              image 'vikas4goyal/aws-sam:0.0.1'
            }

          }
          steps {
            sleep 10
            sh 'mkdir -p build/YBAAuthorizer && touch build/YBAAuthorizer/myfile.txt'
            sh 'ls build/YBAAuthorizer'
            stash(name: 'stage-1', includes: '${pwd}/build/*')
          }
        }

        stage('Stage 2') {
          agent {
            docker {
              image 'vikas4goyal/aws-sam:0.0.1'
              args '-v /var/run/docker.sock:/var/run/docker.sock'
            }

          }
          steps {
            sleep 10
            sh 'mkdir -p build/Login && touch build/Login/myfile.txt'
            stash(includes: 'build/*', name: 'stage-2')
          }
        }

        stage('Stage 3') {
          agent {
            docker {
              args '-v /var/run/docker.sock:/var/run/docker.sock'
              image 'vikas4goyal/aws-sam:0.0.1'
            }

          }
          steps {
            sleep 20
            echo 'I am Awake'
            sh 'mkdir -p build/Register && touch build/Register/myfile.txt'
            stash(includes: 'build/*', name: 'stage-3')
          }
        }

      }
    }

    stage('After') {
      agent {
        docker {
          image 'vikas4goyal/aws-sam:0.0.1'
          args '-v /var/run/docker.sock:/var/run/docker.sock'
        }

      }
      steps {
        sleep 30
        echo 'All Step Done'
        dir(path: 'build/') {
          unstash 'stage-1'
          unstash 'stage-2'
          unstash 'stage-3'
          sh 'pwd'
          sh 'ls'
        }

        sh 'ls'
        sh 'pwd'
      }
    }

  }
}