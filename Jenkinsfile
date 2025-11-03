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

        stage('Deploy') {
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
    }

    post {
        always {
            echo "Pipeline completed for branch: ${env.BRANCH_NAME}"
        }
    }
}
