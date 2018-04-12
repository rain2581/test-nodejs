#!/usr/bin/groovy

def kubectlTest() {
    // Test that kubectl can correctly communication with the Kubernetes API
    println "checking kubectl connnectivity to the API"
    sh "kubectl get nodes"

}

def helmConfig() {
    //setup helm connectivity to Kubernetes API and Tiller
    println "initiliazing helm client"
    println "checking client/server version"
    sh "kubectl version"
    sh "kubectl get namaspaces"
    sh "helm version"
    sh "helm list"
}

podTemplate(label: 'jenkins-pipeline', containers: [
    containerTemplate(name: 'helm', image: 'konstantin2581/jenkins-slave-kubectl-helm:v1.0.0', command: 'cat', ttyEnabled: true),
]) {
node ('jenkins-pipeline') {

checkout scm
stage ('test deployment') {
 println "Runing kubectl/helm tests"
//      container('kubectl') {
//        kubectlTest()
//      }
      container('helm') {
        helmConfig()
      }

}
}
}
