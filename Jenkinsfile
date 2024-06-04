pipeline {
  agent any

  stages {
    stage('Build') {
      steps {
        script {
          def buildOutput = sh(script: 'mvn clean package', returnStdout: true).trim()
          echo "Build Stage Output:\n ${buildOutput}"  // This line is for demonstration only, remove in production
          mail to: 'adityabanerjee992@gmail.com',
              subject: "Pipeline Build Output",
              body: "Build Stage Output:\n ${buildOutput}"
        }
      }
    }
    stage('Unit and Integration Tests') {
      steps {
        script {
          def testOutput = sh(script: 'mvn test', returnStdout: true).trim()
          echo "Test Stage Output:\n ${testOutput}"  // This line is for demonstration only, remove in production
          mail to: 'adityabanerjee992@gmail.com',
              subject: "Pipeline Test Output",
              body: "Test Stage Output:\n ${testOutput}"
        }
      }
    }
    stage('Deploy to Staging') {
      steps {
        script {
          echo 'Deploy to staging'
          // Add your deployment commands here
        }
      }
    }
    stage('Integration Tests on Staging') {
      steps {
        script {
          echo 'Run integration tests on staging'
          // Add your integration test commands here
        }
      }
    }
    stage('Deploy to Production') {
      steps {
        script {
          echo 'Deploy to production'
          // Add your deployment commands here
        }
      }
    }
  }

  post {
    success {
      mail to: 'adityabanerjee992@gmail.com',
          subject: "Pipeline Success",
          body: "Build succeeded."
    }
    failure {
      mail to: 'adityabanerjee992@gmail.com',
          subject: "Pipeline Failure",
          body: "Build failed."
    }
  }
}
