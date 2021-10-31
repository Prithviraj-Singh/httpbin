/*pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t prithvirajsingh1604/demo:"$BUILD_NUMBER"'
            }
        }
        stage('debug') {
            steps {
                sh 
            }
        }
    }
}
*/
pipeline { 

    environment { 

        registry = "prithvirajsingh1604/demo" 

        registryCredential = 'dockerhub' 

        dockerImage = '' 

    }
    agent any 

    stages { 

        stage('Building our image') { 

            steps { 

                script { 

                    dockerImage = docker.build registry + ":$BUILD_NUMBER" 

                }

            } 

        }

        stage('Deploy our image') { 

            steps { 

                script { 

                    docker.withRegistry( '', registryCredential ) { 

                        dockerImage.push() 

                    }
                } 

            }

        } 

        stage('Cleaning up') { 

            steps { 

                sh "docker rmi $registry:$BUILD_NUMBER" 

            }

        } 

    }

}
