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
    stage('Upload to AWS') {
      steps {
        withAWS(region:'ap-northeast-1',credentials:'aws-static') {
          s3Upload(pathStyleAccessEnabled:true, payloadSigningEnabled: true, file:'index.html', bucket:'udacity-michlin0825-jenkins', path:'index.html')
        }
      } 
    }
  }
}