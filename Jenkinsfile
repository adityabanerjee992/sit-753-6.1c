pipeline {
  agent any

  stages {
    stage('Build') {
      steps {
        script {
          def buildOutput = captureOutput(text: 'mvn clean package', returnStdout: true)
          // Send the entire console output (logs) in success email (no changes needed)
          mail to: 'adityabanerjee992@gmail.com',
              subject: "Pipeline Build Output",
              body: "Build Stage Output:\n ${buildOutput}"
        }
      }
    }
    stage('Unit and Integration Tests') {
      steps {
        script {
          def testOutput = captureOutput(text: 'mvn test', returnStdout: true)
          // Send the entire console output (logs) in success email (no changes needed)
          mail to: 'adityabanerjee992@gmail.com',
              subject: "Pipeline Test Output",
              body: "Test Stage Output:\n ${testOutput}"
        }
      }
    }
    stage('Deploy to Staging') {
      steps {
        // Deploy to staging
        echo 'deploy to staging'
      }
    }
    stage('Integration Tests on Staging') {
      steps {
        // Run integration tests on staging
        echo 'run integrations test'
      }
    }
    stage('Deploy to Production') {
      steps {
        // Deploy to production
        echo 'deploy to prod'
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
