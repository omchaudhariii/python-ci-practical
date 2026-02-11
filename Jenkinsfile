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
                bat '''
                    python -m pip install --upgrade pip
                    python -m pip install -r requirements.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                bat '''
                    python -m pytest -q
                '''
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
