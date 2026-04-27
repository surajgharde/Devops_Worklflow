pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myapp .'
            }
        }

        stage('Free Port 5000') {
            steps {
                sh '''
                docker ps -q --filter "publish=5000" | xargs -r docker stop
                docker ps -aq --filter "publish=5000" | xargs -r docker rm
                '''
            }
        }

        stage('Remove Old Container Name') {
            steps {
                sh 'docker rm -f mycontainer || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 5000:5000 --name mycontainer myapp'
            }
        }
    }
}