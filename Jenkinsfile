pipeline {
    agent any

    stages {
        stage('Check for Changes') {
            when {
                expression { return env.BRANCH_NAME == 'feature' || env.BRANCH_NAME == 'master' || env.BRANCH_NAME == 'third' }
            }
            steps {
                script {
                    def hasChanges = false
                    try {
                        // Check if there are any changes in the current branch
                        hasChanges = sh(returnStatus: true, script: 'git diff --quiet HEAD~ HEAD')
                    } catch (Exception ex) {
                        currentBuild.result = 'FAILURE'
                        error "Failed to check for changes: ${ex}"
                    }

                    if (hasChanges) {
                        echo "Changes detected in ${env.BRANCH_NAME}"
                    } else {
                        echo "No changes detected in ${env.BRANCH_NAME}"
                    }
                }
            }
        }
    }
}
