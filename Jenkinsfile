pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building..'
        sh '''
                echo "doing build stuff.."
                '''
      }
    }

    stage('Test') {
      parallel {
        stage('Test') {
          steps {
            echo 'Testing..'
            sh '''
                echo "doing test stuff.."
                '''
          }
        }

        stage('buildFile') {
          steps {
            sh '''touch hello.txt 

echo "beastmaster" >>hello,txt
'''
          }
        }

      }
    }

    stage('Deploye') {
      steps {
        echo 'Deliver....'
        sh '''docker build -t my-small-image .

echo "doing delivery stuff with docker.."
                '''
      }
    }

    stage('Deliver') {
      steps {
        echo 'Deliver Completed'
        sh 'echo "Pipeline completed"'
      }
    }

  }
}