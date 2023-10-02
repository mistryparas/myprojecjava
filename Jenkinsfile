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
      stage("Env create") {
        steps {
          sh ''' mkdir -p pkg
          mv target/demo.war pkg/demo.war
          '''
        }
      }
      stage ("Docker Build") {
        steps {
          sh ''' docker build -t project-demo:3.\${BUILD_NUMBER} .'''
        }
      }


    }
}