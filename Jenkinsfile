pipeline{
  agent any
  stages{
    stage('checkout'){
      steps{
        echo "This is the checkout stage"
      }
    }
    stage('create a container'){
      steps{
      sh 'docker create --name demo-container1 busybox'
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
