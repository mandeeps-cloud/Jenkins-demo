pipeline{
    agent{
        dockerfile{
     }
  }
}

stage{ name = "push"
   steps{ }
}
withCredentials([file(credentialsId: 'kubernetes', variable: 'GC_KEY')]){
              sh "cat '$GC_KEY' | docker login -u _json_key --password-stdin https://eu.gcr.io"
              sh "gcloud auth activate-service-account --key-file='$GC_KEY'"
              sh "gcloud auth configure-docker"
              GLOUD_AUTH = sh (
                    script: 'gcloud auth print-access-token',
                    returnStdout: true
                ).trim()
              echo "Pushing image To GCR"
              sh "docker push us.gcr.io/${google_projectname}/${image_name}:${image-tag}"
              echo "Pushing image To GCR"
              }

//         Docker{
//             image 'ubuntu:latest'
//             command 'bash -c "while true; do echo hello; sleep 1; done"'
//         }
//     }

// }