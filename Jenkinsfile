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
            sh '''echo "Checking For DSF"
sleep 5s'''
          }
        }

        stage('checkwarfile') {
          steps {
            sh '''echo \'jar -tvf target/dsf-iris.war | grep dsf.properties\'

echo \'jar xvf target/dsf-iris.war WEB-INF\\classes\\dsf.properties\'
jar xvf /home/guru/poctarget/irf-test-web.war WEB-INF/classes/jms.properties 
grep \'t24.security.context=INPUTT/123456\' WEB-INF/classes/jms.properties 
sleep 10s


'''
          }
        }

        stage('build') {
          steps {
            sh '''echo "copy target"
cp /home/guru/poctarget/irf-test-web.war /home/guru/poctarget/copytarget 
sleep 20s'''
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