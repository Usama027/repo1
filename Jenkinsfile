def qaPipeline = env.TEST_TEXT?.contains('[qa]')?: false

def matcher = (env.TEST_TEXT =~ /\[qa\]/i) 
// def qaPipeline (text) {
//     if (env.TEST_TEXT == null) {
//         return false
//     }
//     text = text.toLowerCase()
//     return text.contains('[qa]')
// }

// def hasQaTag(text) {
//     return text?.contains('[qa]')
// }
// def result = hasQaTag(env.TEST_TEXT)

// def qaPipeline(text) {
//     if (text != text.toLowerCase().contains('[qa]') {
//         return false
//     }

// }

pipeline {
    agent any
    
    environment {
        TEST_TEXT     = "any text with or without qa [qa]"
        
    }
    stages {
        stage('Build') {
            steps {
                echo "Building on branch: ${env.BRANCH_NAME}"
                echo  ">>>>>>>>>>>>>> ${qaPipeline}"
                echo  ">>>>>>>>>>>>>> matcher
                echo  ">>>>>>>>>>>>>> ${matcher}

            }
        }

    stage('Deploy to Production') {
        when {
            branch 'repo1'

        allOf {
                // expression { qaPipeline(env.TEST_TEXT) != false }
             // expression {${env.TEST_TEXT?.toLowerCase()?.contains('[qa]')}" != false}}
            expression { ${env.TEST_TEXT?.contains('[qa]')}}
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
