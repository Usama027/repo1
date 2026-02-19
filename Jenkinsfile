// def skipQaPipeline = env.TEST_TEXT?.toLowerCase()?.contains('[qa]') ?: false
pipeline {
    agent any
    
    environment {
        TEST_TEXT     = 'any text with or without qa'
    }

    parameters {
        choice(name: 'ENVIRONMENT', choices: ['dev', 'test', 'prod'], description: 'Select environment')
    }
    stage('Deploy') {
            steps {
                echo "Deploying to environment: ${params.ENVIRONMENT}"
                // Add deployment steps here
            }
    }
    
    stages {
        stage('Build') {
            steps {
                echo "Building on branch: ${env.BRANCH_NAME}"
            }
        }
    
        stage('Deploy to Production') {
            when {
                branch 'repo1'
            allOf {
                // expression { qaPipeline.toBoolean() }
                // expression { (env.TEST_TEXT?.toLowerCase()?.contains('[qa]') ?: false }
                // expression {env.TEST_TEXT != null && env.TEST_TEXT?.toLowerCase()?.contains('[qa]') }
                // expression {env.TEST_TEXT != null}

            }
            steps {
                echo 'Deploying to repo1 #####################################...'
                // Add production deployment steps here
            }
        }
        }

        stage('Integration Tests') {
            when {
                branch 'repo2'
            }
            steps {
                echo 'Deploying to repo1 #####################################...'
                // Add integration test steps here
            }
        }
    }
}
