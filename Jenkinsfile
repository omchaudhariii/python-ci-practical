pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                    python3 -m pip install --upgrade pip
                    python3 -m pip install -r requirements.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh 'python3 -m pytest -q'
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: Tests passed'
        }
        failure {
            echo 'FAILED: Check console output'
        }
    }
}
