pipeline {
  agent any
  stages {
    stage('build') {
      environment {
        env_03 = '3'
        env_04 = '4'
      }
      parallel {
        stage('build') {
          agent any
          environment {
            env_01 = '1'
          }
          steps {
            echo 'build'
            echo 'env.env_01'
            build(job: 'test_py', propagate: true)
            echo 'env.PATH'
            echo "BUILD_ID =  Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
            sh 'sh \'python --version\''
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
        echo '${env_02}'
        echo '${env_01}'
        build 'print_hello'
        build(job: 'test_py', propagate: true)
      }
    }
  }
}