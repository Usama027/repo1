pipeline {
    agent any

    environment {
        TEST_TEXT = 'any text with or without qa'
    }

    stages {
        stage('Build') {
            steps {
                echo "Building on branch: ${env.BRANCH_NAME}"
            }
        }

        stage('Deploy to Production') {
            when {
                allOf {
                    branch 'repo1'
                    // expression { env.TEST_TEXT?.toLowerCase()?.contains('[qa]') ?: false }
                    // expression { env.TEST_TEXT != null && env.TEST_TEXT?.toLowerCase()?.contains('[qa]') }
                        expression {env.TEST_TEXT != 'false'}
                }
            }
            steps {
                echo 'Deploying to repo1 #####################################...'
                // Add production deployment steps here
            }
        }

        stage('Integration Tests') {
            when {
                branch 'repo2'
            }
            steps {
                echo 'Running integration tests...'
                // Add integration test steps here
            }
        }
    }
}
