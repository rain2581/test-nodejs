def kubectlTest() {
    // Test that kubectl can correctly communication with the Kubernetes API
    echo "running kubectl test"
    sh "kubectl get nodes"
}

def helmLint(String chart_dir) {
    // lint helm chart
    sh "/usr/local/bin/helm lint ${chart_dir}"

}

def helmDeploy(Map args) {
    //configure helm client and confirm tiller process is installed

    if (args.dry_run) {
        println "Running dry-run deployment"

        sh "/usr/local/bin/helm upgrade --dry-run --debug --install ${args.name} ${args.chart_dir} --set ImageTag=${args.tag},Replicas=${args.replicas} --namespace=${args.name}"
    } else {
        println "Running deployment"
        sh "/usr/local/bin/helm upgrade --install ${args.name} ${args.chart_dir} --set ImageTag=${args.tag},Replicas=${args.replicas} --namespace=${args.name}"

        echo "Application ${args.name} successfully deployed. Use helm status ${args.name} to check"
    }
}
pipeline {
  agent { node { label 'master' } }
    
  stages {
    stage('helm test') {
      steps {
     // run helm chart linter
      helmLint(chart_dir)

    // run dry-run helm chart installation
      helmDeploy(
        dry_run       : true,
        name          : config.app.name,
        chart_dir     : chart_dir,
        tag           : build_tag,
        replicas      : config.app.replicas,
       )
      }
    }
    
    stage ('helm deploy') {
      steps {
      // Deploy using Helm chart
      helmDeploy(
        dry_run       : false,
        name          : config.app.name,
        chart_dir     : chart_dir,
        tag           : build_tag,
        replicas      : config.app.replicas,
      )
     }
     }
    }
    
  }
