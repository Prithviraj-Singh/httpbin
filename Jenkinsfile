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
                echo 'docker build -t prithvirajsingh1604/demo:"$BUILD_NUMBER"'
            }
        }
        stage('debug') {
            steps {
                echo "$image"
            }
        }
    }
}
