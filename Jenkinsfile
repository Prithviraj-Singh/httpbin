pipeline {
    environment { 
        registry = "prithvirajsingh1604/demo" 

        registryCredential = 'dockerhub' 

        dockerImage = '' 

    }
    agent any 

    stages { 
        
        stage('Build') { 

            steps { 

                script { 

                    dockerImage = docker.build registry

                }

            } 

        }

        stage('Pushing') { 

            steps { 

                script { 

                    docker.withRegistry( '', registryCredential ) { 

                        dockerImage.push() 
                    }
                } 
            }
        }
        stage('dep') {
            steps {
                sh 'sudo /home/ec2-user/bin/kubectl apply -f deployment.yml'
            }
        }
        stage('Deploy') {
            steps {
                withKubeConfig([credentialsId: 'kube']) {
                    sh 'sudo /home/ec2-user/bin/kubectl apply -f service.yml'
                }
            }
        }
    }
}
