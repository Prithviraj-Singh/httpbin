pipeline {
    environment {
        hi = "hello"
    }
    agent any

    stages {
        stage('Build') {
            steps {
                echo '$BUILD_NUMBER'
            }
        }
    }
}
