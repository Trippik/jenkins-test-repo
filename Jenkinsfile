pipeline {
    environment {
        imagename = "trippik/jenkins-test"
        registryCredential = "dockerhub"
        dockerImage = ''
    }
    agent any
    stages {
        stage('Build Image') {
            steps {
                script {
                    dockerImage = docker.build imagename
                }
            }
        }
        stage('Upload Image') {
            steps {
                script {
                    docker.withRegistry( '', registryCredential ) {
                    dockerImage.push("$BUILD_NUMBER")
                    dockerImage.push('latest')
                }
            }
        } 
    }
}
