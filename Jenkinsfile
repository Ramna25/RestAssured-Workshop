pipeline {
  agent any
}

stages {
  stage('Trigger based on branch changes') {
    when {
      expression { return BRANCH_NAME == 'master' || BRANCH_NAME == 'feature' || BRANCH_NAME == 'fourth' }
    }
    steps {
      script {
        echo "Changes detected in branch ${env.BRANCH_NAME}"
        
        if (BRANCH_NAME == 'master') {
          echo "Changes in branch a"
        } else if (BRANCH_NAME == 'feature') {
          echo "Changes in branch b"
        } else if (BRANCH_NAME == 'fourth') {
          echo "Changes in branch c"
        }
      }
    }
  }
}
