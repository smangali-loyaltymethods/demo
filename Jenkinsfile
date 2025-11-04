pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo "Building branch: ${env.BRANCH_NAME}"
            }
        }

        stage('Test') {
            steps {
                echo "Running tests on branch: ${env.BRANCH_NAME}"
            }
        }

        stage('Deploy to Production') {
            when {
                branch 'master'
            }
            steps {
                echo "Deploying to Production!"
                // Add production deployment commands here
            }
        }

        stage('Deploy to Staging') {
            when {
                branch 'BranchB'
            }
            steps {
                echo "Deploying to Staging!"
                // Add staging deployment commands here
            }
        }

        stage('Docker Operations for BranchA') {
            when {
                branch 'BranchA'
            }
            stages {
                stage('Checkout') {
                    steps {
                        echo "This is the checkout stage"
                    }
                }

                stage('Create Container') {
                    steps {
                        sh 'docker inspect demo-container1 >/dev/null 2>&1 || docker create --name demo-container1 busybox sleep infinity'
                    }
                }

                stage('Run Container') {
                    steps {
                        sh 'docker start demo-container1'
                    }
                }

                stage('Check Container') {
                    steps {
                        sh 'docker ps -a'
                    }
                }

                stage('Remove Container') {
                    steps {
                        sh '''
                            docker stop demo-container1 || true
                            docker rm demo-container1 || true
                        '''
                    }
                }
            }
        }
    }

    post {
        always {
            echo "Pipeline completed for branch: ${env.BRANCH_NAME}"
        }
    }
}
