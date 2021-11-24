def image

pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    image = docker.build("sixeyed/pi:psod-pipelines","--pull -f Dockerfile")
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