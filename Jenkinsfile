pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '{ IFS=:; ls -H $PATH; } | sort'
        sh 'zip dist *.sh'
        archiveArtifacts(fingerprint: true, onlyIfSuccessful: true, artifacts: 'dist.zip')
      }
    }
    stage('Test') {
      steps {
        sh 'mkdir test'
        sh 'cd test; unzip ../dist.zip; ls'
        input 'Is this approved'
      }
    }
    stage('Deploy') {
      steps {
        sh 'env'
      }
    }
  }
}