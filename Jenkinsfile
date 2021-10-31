pipeline {
    environment {
        hi = "hello"
    }
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'cat Dockerfile'
            }
        }
    }
}
