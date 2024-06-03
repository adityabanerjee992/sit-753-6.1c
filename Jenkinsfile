pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Example build tool
                sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                // Example test tools
                sh 'mvn test'
            }
        }
        stage('Code Analysis') {
            steps {
                // Example code analysis tool
                sh 'sonar-scanner'
            }
        }
        stage('Security Scan') {
            steps {
                // Example security scan tool
                sh 'dependency-check --project JenkinsPipeline --scan .'
            }
        }
        stage('Deploy to Staging') {
            steps {
                // Example deploy to staging
                sh 'scp target/*.jar user@staging-server:/path/to/deploy'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                // Example integration tests on staging
                sh 'mvn verify -Pstaging'
            }
        }
        stage('Deploy to Production') {
            steps {
                // Example deploy to production
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
