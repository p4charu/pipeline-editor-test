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
      parallel {
        stage('Test') {
          steps {
            echo 'Testing..'
          }
        }
        stage('p4') {
          steps {
            p4sync(credential: 'LocalPerforce', depotPath: '//depot/projB/...')
          }
        }
      }
    }
    stage('Deploy') {
      parallel {
        stage('Deploy') {
          steps {
            echo 'Deploying....'
          }
        }
        stage('p4teststage') {
          steps {
            p4sync 'p4poke'
            p4tag(rawLabelName: 'SomeLabel', rawLabelDesc: 'Some description')
          }
        }
      }
    }
  }
}