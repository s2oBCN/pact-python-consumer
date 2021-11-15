pipeline {
    agent {
        dockerfile true
    }
    stages {
        stage('Build') {
            steps {
                sh 'pipenv install -r requirements.txt'
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