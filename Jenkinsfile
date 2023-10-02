pipeline
{
    agent {
      label 'maven'
    }
     stages {
        stage("Checkout") {
      	steps {
          checkout([$class: 'GitSCM',
          branches: [[name: '*/deployment']],
          extensions: [],
          userRemoteConfigs: [[url: 'https://github.com/mistryparas/myprojecjava.git']]]
          )
        }
      }
      stage("Build") {
          steps {
             sh  '''mvn clean package '''
          }
        }


    }
}