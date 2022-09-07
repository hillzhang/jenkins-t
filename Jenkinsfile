pipeline {
  agent any
  environment {
        K8S_CONFIG = credentials('kubeconfig')
    }
    stages{
        stage('init'){
        steps{
            checkout([$class: 'GitSCM', branches: [[name: 'main']], extensions: [], userRemoteConfigs: [[credentialsId: '61053761-cf96-40bf-b2d5-bbab9ab22b07', url: 'https://github.com/hillzhang/jenkins-t.git']]])
        }
        }
        stage('deploy'){
            steps{
                sh "echo ${K8S_CONFIG} |base64 -d > ~/.kube/config"
                sh "kubectl create -f nginx.yaml"
            }
        }
    
    }
}
