pipeline {
  agent {
    docker {
      image 'fpoussin/jenkins:ubuntu-18.04-arm'
    }

  }
  stages {
    stage('Submodules') {
      steps {
        sh '''cd $WORKSPACE/code
git submodule update --init'''
      }
    }
    stage('Build') {
      steps {
        sh '''cd $WORKSPACE/code
nice make -j $(nproc)'''
      }
    }
  }
}