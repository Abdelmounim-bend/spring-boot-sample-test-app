pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'build'
      }
    }

    stage('test') {
      parallel {
        stage('test') {
          steps {
            echo 'test d\'idriss '
          }
        }

        stage('test fonctionelle') {
          steps {
            echo 'test fonctionnel'
          }
        }

        stage('test integration') {
          steps {
            echo 'test int�gration'
          }
        }

      }
    }

    stage('d�ploi') {
      steps {
        echo 'stage deploy'
      }
    }

  }
}