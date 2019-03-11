pipeline {
  agent {
    docker {
      image 'fpoussin/jenkins:ubuntu-18.04-chibios'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh '''git config --file=.gitmodules submodule.code/ChibiOS.url /var/lib/git/ChibiOS
git submodule sync
git submodule update --init || true

git checkout .gitmodules
git submodule sync
git submodule update --init
'''
        sh '''cd $WORKSPACE/code
nice make -j $(nproc)'''
      }
    }
  }
}