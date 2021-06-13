pipeline {
    agent any
    environment{
        SERVICE_NAME = "Testing_Service"
        HELM_INSTALL_RELEASE_NAME = "${SERVICE_NAME}-install"
        HELM_INSTALL_NAMESPACE = "${HELM_INSTALL_RELEASE_NAME}" 
        KUBECTL_CMD = "docker run --rm -v ${WORKSPACE}/.kube/config:/root/.kube/config -v ${WORKSPACE}:${WORKSPACE} bitnami/kubectl:latest"
    }
    stages {
        stage('Clean'){
            steps{
                sh '''
                    echo "Cleanup workspace"
                    chmod -fR 777 "${WORKSPACE}"
                    rm -Rf ./*
                '''
                echo 'SCM Checkout'
                checkout scm                
            }
        }
    }
}    
