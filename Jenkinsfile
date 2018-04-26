node('node') {
  try {
    // Export environment variables pointing to the directory where Go was installed
    withEnv(["GOROOT=${WORKSPACE}"]) {
      sh 'go version'
    }

    // Install the desired Go version
    def root = tool name: 'Go 1.10', type: 'go'


    stage('Checkout') {
      checkout scm
    }

    stage('Test') {
      withEnv(["GOROOT=${WORKSPACE}"]) {
        sh 'go version'
        sh 'make build-dev-deps lint'
      }
    }

    stage('Build Docker') {
        print 'Build'
    }

    stage('Deploy') {
        print 'Deploy'
    }

    stage('Cleanup') {
      print 'prune and cleanup'
    }
  }

  catch (err) {
    currentBuild.result = "FAILURE"
    throw err
  }
}
