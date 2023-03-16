pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'build'
        bat 'mvn -DskipTests clean package'
        archiveArtifacts '**/target/*.jar'
      }
    }

    stage('test') {
      parallel {
        stage('test') {
          steps {
            echo 'test d\'idriss '
            bat 'mvn -Dest="com.example.testigweb.smoke.**" test'
            junit '**/target/surefire-reports/TEST-*.xml'
          }
        }

        stage('integration') {
          steps {
            echo 'test fonctionnel'
            bat 'mvn -Dtest="com.example.testingweb.integration.**" test'
          }
        }

        stage('functional') {
          steps {
            echo 'test intégration'
            bat 'mvn -Dtest="com.example.testingweb.integration.**" test'
          }
        }

      }
    }

    stage('deploy') {
      steps {
        input(message: 'voulez vous continuez', ok: 'lets go')
        echo 'stage deploy'
        bat 'mvn -DskipTests install'
      }
    }

  }
}