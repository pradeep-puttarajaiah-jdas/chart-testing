pipeline {
   agent any
   stages {
    stage('Checkout') {
      steps {
        script {
           // The below will clone your repo and will be checked out to master branch by default.
           git credentialsId: 'pradeep-puttarajaiah-jdas', url: 'https://github.com/pradeep-puttarajaiah-jdas/helm.git'
           // Do a ls -lart to view all the files are cloned. It will be clonned. This is just for you to be sure about it.
           sh "ls -lart ./*" 
           // List all branches in your repo. 
           sh "git branch -a"
           sh 'helm list'
          }
       }
    }
  }
}


pipeline {
   agent any
   stages {
    stage('Checkout') {
      steps {
        script {
           // The below will clone your repo and will be checked out to master branch by default.
           git credentialsId: 'pradeep-puttarajaiah-jdas', url: 'https://github.com/pradeep-puttarajaiah-jdas/helm.git'
           // Do a ls -lart to view all the files are cloned. It will be clonned. This is just for you to be sure about it.
           sh "ls -lart ./*" 
           // List all branches in your repo. 
           sh "git branch -a"
           // Linting
           sh 'helm lint'
           // Chart testing
           sh 'helm test my-release'
          }
       }
    }
  }
}

pipeline {
   agent any
   stages {
    stage('Checkout') {
      steps {
        script {
           // The below will clone your repo and will be checked out to master branch by default.
           git credentialsId: 'pradeep-puttarajaiah-jdas', url: 'https://github.com/pradeep-puttarajaiah-jdas/helm.git'
           // Do a ls -lart to view all the files are cloned. It will be clonned. This is just for you to be sure about it.
           sh "ls -lart ./*" 
        }
      }
    }
    stage('Linting') {
       steps {
          script {
             sh 'helm lint'
          }
       }
    }
    stage('Chart-testing') {
       steps {
          script {
             sh 'helm test my-release'
          }
       }
    }
   }
}


C:\helm\windows-amd64>helm install quirky-walrus wordpress --namespace default
NAME: quirky-walrus
LAST DEPLOYED: Tue Jun 30 23:15:42 2020
NAMESPACE: default
STATUS: deployed
REVISION: 1
NOTES:
** Please be patient while the chart is being deployed **

To access your WordPress site from outside the cluster follow the steps below:

1. Get the WordPress URL by running these commands:

  NOTE: It may take a few minutes for the LoadBalancer IP to be available.
        Watch the status with: 'kubectl get svc --namespace default -w quirky-walrus-wordpress'

   export SERVICE_IP=$(kubectl get svc --namespace default quirky-walrus-wordpress --template "{{ range (index .status.loadBalancer.ingress 0) }}{{.}}{{ end }}")
   echo "WordPress URL: http://$SERVICE_IP/"
   echo "WordPress Admin URL: http://$SERVICE_IP/admin"

2. Open a browser and access WordPress using the obtained URL.

3. Login with the following credentials below to see your blog:

  echo Username: user
  echo Password: $(kubectl get secret --namespace default quirky-walrus-wordpress -o jsonpath="{.data.wordpress-password}" | base64 --decode)

C:\helm\windows-amd64>helm test quirky-walrus
Pod quirky-walrus-credentials-test pending
Pod quirky-walrus-credentials-test succeeded
Pod quirky-walrus-mariadb-test-qo2ir pending
Pod quirky-walrus-mariadb-test-qo2ir pending
Pod quirky-walrus-mariadb-test-qo2ir succeeded
NAME: quirky-walrus
LAST DEPLOYED: Tue Jun 30 23:15:42 2020
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE:     quirky-walrus-mariadb-test-qo2ir
Last Started:   Tue Jun 30 23:23:58 2020
Last Completed: Tue Jun 30 23:24:33 2020
Phase:          Succeeded
TEST SUITE:     quirky-walrus-credentials-test
Last Started:   Tue Jun 30 23:23:50 2020
Last Completed: Tue Jun 30 23:23:58 2020
Phase:          Succeeded
NOTES:
** Please be patient while the chart is being deployed **

To access your WordPress site from outside the cluster follow the steps below:

1. Get the WordPress URL by running these commands:

  NOTE: It may take a few minutes for the LoadBalancer IP to be available.
        Watch the status with: 'kubectl get svc --namespace default -w quirky-walrus-wordpress'

   export SERVICE_IP=$(kubectl get svc --namespace default quirky-walrus-wordpress --template "{{ range (index .status.loadBalancer.ingress 0) }}{{.}}{{ end }}")
   echo "WordPress URL: http://$SERVICE_IP/"
   echo "WordPress Admin URL: http://$SERVICE_IP/admin"

2. Open a browser and access WordPress using the obtained URL.

3. Login with the following credentials below to see your blog:

  echo Username: user
  echo Password: $(kubectl get secret --namespace default quirky-walrus-wordpress -o jsonpath="{.data.wordpress-password}" | base64 --decode)

