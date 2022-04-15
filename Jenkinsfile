pipeline {
  agent {
    node {
      label 'estjbase'
    }

  }
  stages {
    stage('checkenvironment') {
      steps {
        sh 'echo "Checking For DSF"'
        sh '''echo \'check for catalog service host\'
grep \'-Ddsf.catalogService.host=http://10.98.193.104:8080\' /home/guru/poctarget/startup.sh'''
        sh '''echo \'failure poc for catalog service\'
grep \'-Ddsf.catalogService.host=http://10.98.193.104:8080\' /home/guru/poctarget/startupfail.sh'''
      }
    }

  }
}