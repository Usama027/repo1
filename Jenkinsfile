pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Building on branch: ${env.BRANCH_NAME}"
            }
        }

        stage('Deploy to Production') {
            when {
                branch 'branch1'
            }
            steps {
                echo 'Deploying to repo1 #####################################...'
                // Add production deployment steps here
            }
        }

        stage('Integration Tests') {
            when {
                branch 'branch2'
            }
            steps {
                echo 'Deploying to repo1 #####################################...'
                // Add integration test steps here
            }
        }
    }
}
