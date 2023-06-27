pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            echo 'Building..'
            sh '''
                echo "doing build stuff.."
                '''
          }
        }

        stage('parallel') {
          steps {
            sh '''ls -ltr
cat Jenkinnsfile'''
          }
        }

      }
    }

    stage('Test') {
      steps {
        echo 'Testing..'
        sh '''
                echo "doing test stuff.."
                '''
      }
    }

    stage('Deploye') {
      steps {
        echo 'Deliver....'
        sh '''
                echo "doing delivery stuff.."
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