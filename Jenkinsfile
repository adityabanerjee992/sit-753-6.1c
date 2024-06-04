 pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Ensure Maven is installed and configured
                echo 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                // Run unit and integration tests
                echo 'mvn test'
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

