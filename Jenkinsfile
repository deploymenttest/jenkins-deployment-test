pipeline {
    agent { docker { image 'python:3.5.1' } }
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
            post {
                 always {
                     jiraSendBuildInfo site: 'baris-leenders.atlassian.net'
                 }
             }
        }
        stage('Deploy - Staging') {
             when {
                 branch 'staging'
             }
             steps {
                 echo 'Deploying to Staging from the staging branch....'
             }
             post {
                 always {
                     jiraSendDeploymentInfo site: 'baris-leenders.atlassian.net', environmentId: 'staging', environmentName: 'staging', environmentType: 'staging'
                 }
             }
        }
        stage('Deploy - Development') {
             when {
                 branch 'main'
             }
             steps {
                 echo 'Deploying to development from the main branch...'
             }
             post {
                 always {
                     jiraSendDeploymentInfo site: 'baris-leenders.atlassian.net', environmentId: 'development', environmentName: 'development', environmentType: 'development'
                 }
             }
        }
        stage('Deploy - Production') {
             when {
                 branch 'production'
             }
             steps {
                 echo 'Deploying to production from the production branch...'
             }
             post {
                 always {
                     jiraSendDeploymentInfo site: 'baris-leenders.atlassian.net', environmentId: 'production', environmentName: 'production', environmentType: 'production'
                 }
             }
        }
    }
}
