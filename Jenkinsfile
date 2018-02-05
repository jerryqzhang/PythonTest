pipeline {
  agent any
  stages {
    stage('build') {
      parallel {
        stage('build') {
          agent any
          environment {
            env_01 = '1'
          }
          steps {
            echo 'build'
          }
        }
        stage('build2') {
          agent any
          environment {
            env_02 = '2'
          }
          steps {
            echo 'build2'
          }
        }
      }
    }
    stage('test') {
      steps {
        echo 'test'
        echo '${env.env_02}'
      }
    }
  }
}