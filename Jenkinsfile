pipeline {
    agent {
        docker {
            image 'python:3.9.8-alpine3.14'
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
                sh './run_pytest.sh  --junitxml=reports/testReport.xml'
            }
        }
        stage('Publish') {
            steps {
                junit 'reports/testReport.xml'
            }
        }
    }
}