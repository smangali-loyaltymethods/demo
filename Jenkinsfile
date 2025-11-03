pipeline{
  agent any
  stages{
    stage('checkout'){
      steps{
        echo "This is the checkout stage"
      }
    }
    stage('Create Container') {
    steps {
        sh 'docker inspect demo-container1 >/dev/null 2>&1 || docker create --name demo-container1 busybox'
      }
    }

    stage("run the container"){
      steps{
        sh 'docker start demo-container1'
      }
    }
    stage("check container"){
      steps{
        sh 'docker ps'
      }
    }
    stage("remove the container"){
      steps{
        sh 'docker rm demo-container1'
      }
    }

  }
}
