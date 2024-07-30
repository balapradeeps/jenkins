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
            sh '''ls -la 
'''
          }
        }

      }
    }

    stage('Deploye') {
      steps {
        echo 'Deliver....'
        sh '''touch hello.txt
echo "TommyPB" >>hello.txt
cat hello.txt 

docker build -t my-small-image .

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