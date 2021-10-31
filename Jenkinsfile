pipeline {
    environment {
        hi = "hello"
        image = ''
    }
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    image = docker.bulid 'test/test'
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
