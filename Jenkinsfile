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

                    dockerImage = docker.build registry + ":$BUILD_NUMBER" 

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
        stage('Deploy') {
            
            steps {
                script {
                    kubernetesDeploy configs: 'deployment.yml', kubeConfig: [path: ''], kubeconfigId: 'kubeconfig', ssh: [sshCredentialsId: '*', sshServer: ''], textCredentials: [certificateAuthorityData: '', clientCertificateData: '', clientKeyData: '', serverUrl: 'https://']
                }
            }
        }
    }
}
