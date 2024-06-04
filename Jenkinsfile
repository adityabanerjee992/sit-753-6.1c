pipeline {
  agent any

  tools {
    maven 'Maven 3.6.3' // Adjust this to the name you used in Global Tool Configuration
  }

  environment {
    MAVEN_HOME = tool name: 'Maven 3.6.3', type: 'hudson.tasks.Maven$MavenInstallation'
    PATH = "${env.MAVEN_HOME}/bin:${env.PATH}"
  }

  stages {
    stage('Build') {
      steps {
        script {
          buildOutput = sh(script: 'mvn clean package', returnStdout: true).trim()
          writeFile file: 'buildOutput.log', text: buildOutput
          echo "Build Stage Output:\n ${buildOutput}"
        }
      }
    }
    stage('Unit and Integration Tests') {
      steps {
        script {
          testOutput = sh(script: 'mvn test', returnStdout: true).trim()
          writeFile file: 'testOutput.log', text: testOutput
          echo "Test Stage Output:\n ${testOutput}"
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
      script {
        emailext (
          to: 'adityabanerjee992@gmail.com',
          subject: "Pipeline Success",
          body: "Build succeeded.\n\nBuild Stage Output:\n ${buildOutput}\n\nTest Stage Output:\n ${testOutput}",
          attachmentsPattern: 'buildOutput.log,testOutput.log',
          mimeType: 'text/plain'
        )
      }
    }
    failure {
      script {
        emailext (
          to: 'adityabanerjee992@gmail.com',
          subject: "Pipeline Failure",
          body: "Build failed.\n\nBuild Stage Output:\n ${buildOutput}\n\nTest Stage Output:\n ${testOutput}",
          attachmentsPattern: 'buildOutput.log,testOutput.log',
          mimeType: 'text/plain'
        )
      }
    }
  }
}
