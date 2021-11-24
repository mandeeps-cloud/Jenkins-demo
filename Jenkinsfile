def image

pipeline {
    agent {
        label 'docker'
    stages {
        stage('Build') {
            steps {
                script {
                    image = docker.build("Dockerfile")
                }
            }
        }
    }
}
    stage('Smoke Test') {
        steps {
            script {
                container = image.run()
                container.stop()
          }
        }
    }
    stage('Push image') {
        steps {
            script {
                withDockerRegistry([credentialsId: "kubernetes" , url: "https://eu.gcr.io"]) {
                    image.push()
                }
            } 

        }
    }
