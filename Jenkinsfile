pipeline {
  agent any 
  stages {
    stage('Build') {
      steps {
        sh 'echo "Hello World"'
        sh '''
                  echo "Multiline shell steps works too"
                  ls -lah
              '''
      }
    }
  }
}
pipeline {
  agent any
  stages {
    stage('Lint HTML') {
      steps {
        sh 'tidy -q -e *.html'
      }
    stage('Upload to AWS') {
      steps {
        withAWS(region:'us-west-2',credentials:'blueocean') {
          s3Upload(pathStyleAccessEnabled:true, payloadSigningEnabled: true, file:'index.html', bucket:'ha-udacity-webapp-deployment')
        }
      }
    }
  }
}
