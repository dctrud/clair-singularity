pipeline {
  agent {
    docker {
      image 'ubuntu:trusty'
    }
    
  }
  stages {
    stage('Test') {
      steps {
        sh '''sudo apt-get install -y wget
wget -O- http://neuro.debian.net/lists/trusty.us-nh.full | sudo tee /etc/apt/sources.list.d/neurodebian.sources.list
sudo apt-key adv --recv-keys --keyserver hkp://pool.sks-keyservers.net:80 0xA5D32F012649A5A9
sudo apt-get -qq update
sudo apt-get install -y singularity-container
pip install flake8 pytest pytest-cov pytest-flake8 python-coveralls
'''
        sh '''build_scripts/travis_tests.sh
'''
      }
    }
  }
}