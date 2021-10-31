pipeline {
    environment {
        hi = "hello"
        image = ''
        imagename = "test/test"
    }
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    image = docker.bulid imagename
                }
            }
        }
        stage('debug') {
            steps {
                echo "$image"
            }
        }
    }
}
