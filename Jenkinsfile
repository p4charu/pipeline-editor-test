pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            echo 'Building..'
          }
        }
        stage('ParallelBuild') {
          steps {
            git(url: 'https://github.com/p4charu/pipeline-editor-test.git', branch: 'master', credentialsId: 'p4charuGit')
          }
        }
      }
    }
    stage('Test') {
      steps {
        echo 'Testing..'
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying....'
      }
    }
  }
}