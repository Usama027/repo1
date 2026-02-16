// def qaPipeline = env.TEST_TEXT.toString()?.toLowerCase()?.contains('[qa]')?: false
 // def qaPipeline = env.TEST_TEXT?.toString()?.toLowerCase()?.contains("[qa]")?: false
// def qaPipeline = env.TEST_TEXT?.toString()

// def qa  = (env.TEST_TEXT =~ /\[ (.+) ]/)

// def hasQa = (env.TEST_TEXT.toString() =~ /\[qa\]/).find('[qa]')
// def hasQa =(env.TEST_TEXT?.contains('[qa]') =~ /\[qa\].*?\[\/qa\]/).find()
// def hasQa = env.TEST_TEXT?.toString()?.contains('[qa]')?: false
// def hasQa = env.TEST_TEXT?.toString()?.toLowerCase()?.contains('[qa]')?: false
def hasQa = (env.TEST_TEXT )
def found = hasQa.contains("[qa]") // true if found, false otherwise
// def qaPipeline (text) {
//     if (env.TEST_TEXT == null) {
//         return false
//     }
//     text = text.toLowerCase()
//     return text.contains('[qa]')
// }

// def hasQaTag(text) {
//     return text?.toString()?.toLowerCase()?.contains("[qa]")
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
                // echo ">>>>>>> text >>>> : ${result}"
                echo ">>>>>>> text >>>> : ${hasQa}"
                echo ">>>>>>> text >>>> : ${found}"


            }
        }

        stage('Deploy to Production') {
            when {
                branch 'repo1'

            allOf {
                    // expression { qaPipeline(env.TEST_TEXT) != false }
                // expression {${env.TEST_TEXT?.toString()?.toLowerCase()?.contains('[qa]')}" != false}}
                expression { !hasQa}
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
