pipeline {
    agent any
    stages {
      stage('Lint HTML') {
        steps {
          sh 'tidy -q -e *.html'
        }
      }
      stage('Upload to AWS') {
        steps {
          withAWS(region:'us-west-2',credentials:'643968575852') {
            s3Upload(pathStyleAccessEnabled:true, payloadSigningEnabled: true, file:'index.html', bucket:'jenkins-s3-qch')
          }
        }
      }
    }
    }