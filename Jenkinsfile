def kubectlTest() {
    // Test that kubectl can correctly communication with the Kubernetes API
    echo "running kubectl test"
    sh "kubectl get nodes"
}

def helmLint(String chart_dir) {
    // lint helm chart
    sh "/usr/local/bin/helm lint ${chart_dir}"

}

pipeline {
  agent { node { label 'master' } }
    
  stages {
    stage('build') {
      steps {
        sh 'npm install'
      }
    }
  }
}
