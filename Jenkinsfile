pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    image = docker.build("dockerfile")
                }
            }
        }
    }
}

    stage('Push image') {
        steps {
            script {
                withDockerRegistry([credentialsId: "kubernetes" , url: "https://eu.gcr.io"]) {
                    
                def customImage = docker.build("my-image:${env.BUILD_ID}")
                    customimage.push()
                }
            } 

        }
    }



    // stage('Smoke Test') {
    //    steps {
    //         script {
    //             container = image.run()
    //             container.stop()
    //       }
    //     }
    // }

    //         withCredentials([file(credentialsId: 'kubernetes', variable: 'GC_KEY')]){
    //           sh "cat '$GC_KEY' | docker login -u _json_key --password-stdin https://eu.gcr.io"
    //           sh "gcloud auth activate-service-account --key-file='$GC_KEY'"
    //           sh "gcloud auth configure-docker"
    //           GLOUD_AUTH = sh (
    //                 script: 'gcloud auth print-access-token',
    //                 returnStdout: true
    //             ).trim()
    //           echo "Pushing image To GCR"
    //           sh "docker push eu.gcr.io/${gcp-r-d}/${image_name}:${image-tag}"
    //              post { 
    //     always {
    //         script {
    //             if (getContext(hudson.FilePath)) {
    //                 deleteDir()
    //             }
    //         }
    //     }
    // }
    //       }


