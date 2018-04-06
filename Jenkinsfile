
podTemplate(label: 'jenkins-pipeline', containers: [
   containerTemplate(name: 'helm', image: 'lachlanevenson/k8s-helm:v2.6.0', command: 'cat', ttyEnabled: true),
    containerTemplate(name: 'kubectl', image: 'lachlanevenson/k8s-kubectl:v1.4.8', command: 'cat', ttyEnabled: true)
   ]) {
node ('jenkins-pipeline') {
	stage 'Kubectl test'
        container('kubectl') {
          stage 'Get nodes'
          sh 'kubectl get nodes'   
        }
  }
}
