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
            // Install mychart in to cluster
           sh 'helm install -n chart-test'
           // List the releases
           sh 'helm list https://pradeep-puttarajaiah-jdas.github.io/chart-testing/ -n chart-test --generate-name'
           // Chart testing
           sh 'helm test test_chart -n chart-test'
          }
       }
    }
  }
}
