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
            echo '{env.env_02}'
          }
        }
        stage('build2') {
          agent any
          environment {
            env_02 = '2'
          }
          steps {
            echo 'build2'
            timestamps()
          }
        }
      }
    }
    stage('test') {
      steps {
        echo 'test'
      }
    }
  }
}