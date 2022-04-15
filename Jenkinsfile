pipeline {
  agent {
    node {
      label 'estjbaseserver'
    }

  }
  stages {
    stage('checkenvironment') {
      parallel {
        stage('checkenvironment') {
          steps {
            sh 'echo "Checking For DSF"'
          }
        }

        stage('checkin warfiles') {
          steps {
            load '/home/guru/poctarget/source/findClassinJar.groovy'
          }
        }

      }
    }

    stage('checkcatalog env') {
      steps {
        sh '''echo \'check for catalog service host\'
grep \'Ddsf.catalogService.host=http://10.98.193.104:8080\' /home/guru/poctarget/startup.sh'''
      }
    }

    stage('checkcatalog fail') {
      steps {
        sh '''echo \'failure poc for catalog service\'
grep \'Ddsf.catalogService.host=http://10.98.193.104:8080\' /home/guru/poctarget/startupfail.sh'''
      }
    }

  }
}