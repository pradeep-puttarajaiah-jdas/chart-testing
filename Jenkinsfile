pipeline {
   agent any
   stages {
    stage('Checkout') {
      steps {
        script {
           // The below will clone your repo and will be checked out to master branch by default.
           git credentialsId: 'pradeep.puttarajaiah@blueyonder.com', url: 'https://github.com/pradeep-puttarajaiah-jdas/chart-testing.git'
           // Do a ls -lart to view all the files are cloned. It will be clonned. This is just for you to be sure about it.
           sh "ls -lart ./*" 
           // Update repo
           sh 'helm repo update'
           // Linting
           sh 'helm lint'
           // List the releases
           sh 'helm list'
           // Chart testing
           sh 'helm test mychart'
          }
       }
    }
  }
}
