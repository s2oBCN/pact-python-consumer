pipeline {
    agent {
        docker {
            image 'python:3.9.8-slim-buster'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'pip install --no-cache-dir -r requirements.txt'
            }
        }
        stage('Test') {
            steps {
                sh script:'pytest --junitxml=reports/testReport.xml', returnStatus:true
            }
        }
        stage('Publish') {
            steps {
                junit 'reports/testReport.xml'
            }
        }
    }
}