def qaPipeline = env.TEST_TEXT?.toLowerCase()?.contains('[qa]') ?: false
pipeline {
    agent any
    
    environment {
        TEST_TEXT     = "any text with or without qa '[qa]'"
        
    }
    stages {
        stage('Build') {
            steps {
                echo "Building on branch: ${env.BRANCH_NAME}"
                echo  ">>>>>>>>>>>>>> ${qaPipeline}"
            }
        }

    stage('Deploy to Production') {
        when {
            branch 'repo1'

        allOf {
                expression {env.qaPipeline == 'false' }
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
            echo 'Deploying to repo1 #####################################...'
            // Add integration test steps here
        }
    }
    }
}
