// def env ()
def var 
def qa = env.TEST_TEXT?.toLowerCase()?.contains('[qa]') ?: false
          
pipeline {
    agent any

    environment {
        TEST_TEXT = 'any text with or without qa [qa]'
    }

    stages {
        stage('Build') {
            steps {
                echo "Building on branch: ${env.BRANCH_NAME}"
                echo "text >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>: ${env.TEST_TEXT}"

           
            }
        }
        
        
        stage('check env') {
            steps {
                script {
                    def result = env.TEST_TEXT != null && env.TEST_TEXT.toLowerCase().contains('[qa]')
                    echo "Expression result >>>>>>>>>>>>>>: ${result}"
                     var = result.toString()
                    // env.QA_FOUND = result.toString()
                    env.QA_FOUND = result.toString()
                    echo "QA_FOUND >>>>>>>>>>>> ${var} "
                }
                 echo "QA_FOUND_OUT >>>>>>>>>>>> ${var} "
            }
        }


              

        stage('echo var ') {
            steps {

                 echo "QA_FOUND_echo  >>>>>>>>>>>> ${env.QA_FOUND} "

                    echo "QA_FOUND_echo  >>>>>>>>>>>> ${qa} "
            }
        }
              
        
        stage('Deploy to Production') {
            when {
                branch 'repo1'
            }
            steps {
                echo 'Deploying to repo1 #####################11111111111111################...'
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
