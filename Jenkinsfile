pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
               //  git branch: 'master', credentialsId: 'gitcred', url: 'git@github.com:dipalilule/nodejs_app.git'
                git branch: 'master',
    credentialsId: 'gitcred',
    url: 'https://github.com/dipalilule/nodejs_app.git'
            }
  }
        stage('docker build') {
            steps {
                sh """
               docker build --no-cache -t 595552316002.dkr.ecr.ap-south-1.amazonaws.com/nodejs-image-demo:$BUILD_NUMBER .
               aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin 595552316002.dkr.ecr.ap-south-1.amazonaws.com
               docker push 595552316002.dkr.ecr.ap-south-1.amazonaws.com/nodejs-image-demo:$BUILD_NUMBER
               """
            }
        }
        stage('Deploy') {
            steps {
                 sh """
               
                 docker pull 595552316002.dkr.ecr.ap-south-1.amazonaws.com/nodejs-image-demo:$BUILD_NUMBER
                 docker run -p 8000:8081 -d 595552316002.dkr.ecr.ap-south-1.amazonaws.com/nodejs-image-demo:$BUILD_NUMBE

              """
              


            }
        }
    }
}
