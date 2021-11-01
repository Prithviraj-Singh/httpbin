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
        }/*
        stage('dep') {
            steps {
                sh 'sudo kubectl apply -f deployment.yml'
            }
        }*/
        stage('dep') {
            steps {
                withKubeConfig([credentialsId: 'kube']) {
                    sh 'sudo /home/ec2-user/bin/kubectl apply -f deployment.yml'
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
