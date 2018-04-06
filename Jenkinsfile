node {
  stage('List pods') {
    withKubeConfig([credentialsId: '<credential-id>', caCertificate: '<ca-certificate>', serverUrl: '<api-server-address>']) {
      sh 'kubectl get pods'
    }
  }
}
