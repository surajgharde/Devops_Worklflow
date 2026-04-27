pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip3 install flask'
            }
        }

        stage('Run Flask App') {
            steps {
                sh 'nohup python3 app.py > output.log 2>&1 &'
            }
        }
    }
}