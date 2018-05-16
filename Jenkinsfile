pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '{ IFS=:; ls -H $PATH; } | sort'
        sh 'pwd'
        sh 'ls -ltr'
        sh 'tar -cjf  dist.tar.bz2 README.md Jenkinsfile'
        archiveArtifacts(fingerprint: true, onlyIfSuccessful: true, artifacts: 'dist.tar.bz2')
      }
    }
    stage('Test') {
      steps {
        sh 'mkdir test'
        sh 'cd test; tar -xvjf  ../dist.tar.bz2; ls'
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