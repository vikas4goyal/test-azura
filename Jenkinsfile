pipeline {
  agent {
    docker {
      image 'vikas4goyal/aws-sam:0.0.1'
      args '-v /var/run/docker.sock:/var/run/docker.sock -v $(pwd):/opt/src --mount type=bind,source=/tmp,target=/tmp'
    }

  }
  stages {
    stage('Stage 1') {
      parallel {
        stage('Stage 1') {
          steps {
            sleep 30
            echo 'I am awake'
          }
        }

        stage('Stage 2') {
          steps {
            sleep 30
            echo 'I am awake'
          }
        }

        stage('Stage 3') {
          steps {
            sleep 30
            echo 'I am Awake'
          }
        }

        stage('Stage 4') {
          steps {
            sleep 40
            echo 'I am Awake'
          }
        }

        stage('Stage 5') {
          steps {
            sleep 60
            echo 'I am Awake'
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