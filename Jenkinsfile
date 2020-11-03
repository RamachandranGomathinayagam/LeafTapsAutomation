pipeline {
  agent any
  stages {
    stage('Devlopment') {
      steps {
        echo 'Pull the code from the git'
        echo 'Create a build using Git Repo'
      }
    }

    stage('Smoke Test') {
      steps {
        echo 'Run 2 Chrome Test'
      }
    }

    stage('Deploy') {
      steps {
        echo 'Stop the running server'
        echo 'Move the build to QA'
        echo 'Start the server'
        echo 'Notify to QA'
      }
    }

    stage('Integration test') {
      parallel {
        stage('Integration test') {
          steps {
            echo 'Sanity UI Test'
            git(url: 'https://github.com/RamachandranGomathinayagam/LeafTapsAutomation', branch: 'master', poll: true)
            bat 'mvn test'
          }
        }

        stage('API test') {
          steps {
            echo 'Run API test'
          }
        }

        stage('Performance Test') {
          steps {
            echo 'Run Jmeter test'
          }
        }

      }
    }

    stage('Certify') {
      steps {
        echo 'QA certify'
      }
    }

  }
}