pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Create Virtual Environment') {
            steps {
                sh '''
                    python3 -m venv venv
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                    . venv/bin/activate
                    pip install --upgrade pip
                    pip install flask
                '''
            }
        }

        stage('Run Flask App (Test)') {
            steps {
                sh '''
                    . venv/bin/activate
                    python app.py &
                    sleep 10
                    pkill -f app.py || true
                '''
            }
        }
    }

    post {
        success {
            echo "Build Successful 🚀"
        }
        failure {
            echo "Build Failed ❌"
        }
    }
}