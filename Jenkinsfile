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
            sleep 30
            sh 'ls'
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
            sleep 30
            sh 'ls'
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
            sleep 30
            echo 'I am Awake'
          }
        }

        stage('Stage 4') {
          agent {
            docker {
              image 'vikas4goyal/aws-sam:0.0.1'
              args '-v /var/run/docker.sock:/var/run/docker.sock'
            }

          }
          steps {
            sleep 40
            echo 'I am Awake'
          }
        }

        stage('Stage 5') {
          agent {
            docker {
              args '-v /var/run/docker.sock:/var/run/docker.sock'
              image 'vikas4goyal/aws-sam:0.0.1'
            }

          }
          steps {
            sleep 60
            echo 'I am Awake'
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
      }
    }

  }
}