def image

pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    image = docker.build("mcr.microsoft.com/dotnet/core/aspnet:3.1.1")
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