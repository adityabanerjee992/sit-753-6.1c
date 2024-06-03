pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Ensure Maven is installed and configured
                sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                // Run unit and integration tests
                sh 'mvn test'
            }
        }
        stage('Code Analysis') {
            steps {
                // Run code analysis
                sh 'sonar-scanner'
            }
        }
        stage('Security Scan') {
            steps {
                // Run security scan
                sh 'dependency-check --project JenkinsPipeline --scan .'
            }
        }
        stage('Deploy to Staging') {
            steps {
                // Deploy to staging
                sh 'scp target/*.jar user@staging-server:/path/to/deploy'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                // Run integration tests on staging
                sh 'mvn verify -Pstaging'
            }
        }
        stage('Deploy to Production') {
            steps {
                // Deploy to production
                sh 'scp target/*.jar user@production-server:/path/to/deploy'
            }
        }
    }
    post {
        success {
            mail to: 'developer@example.com',
                 subject: "Pipeline Success: ${currentBuild.fullDisplayName}",
                 body: "Build ${currentBuild.fullDisplayName} succeeded."
        }
        failure {
            mail to: 'developer@example.com',
                 subject: "Pipeline Failure: ${currentBuild.fullDisplayName}",
                 body: "Build ${currentBuild.fullDisplayName} failed."
        }
    }
}

