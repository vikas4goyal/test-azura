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
          steps {
            node(label: 'Stage 1') {
              sleep 30
              sh 'ls'
            }

          }
        }

        stage('Stage 2') {
          steps {
            node(label: 'Stage 2 Node') {
              sleep 30
              sh 'ls'
            }

          }
        }

        stage('Stage 3') {
          steps {
            node(label: 'Stage 3 Node') {
              sleep 30
              echo 'I am Awake'
            }

          }
        }

        stage('Stage 4') {
          steps {
            node(label: 'Stage 4 Node') {
              sleep 40
              echo 'I am Awake'
            }

          }
        }

        stage('Stage 5') {
          steps {
            node(label: 'Stage 5 Node') {
              sleep 60
              echo 'I am Awake'
            }

          }
        }

      }
    }

    stage('After') {
      steps {
        sleep 30
        echo 'All Step Done'
      }
    }

  }
}