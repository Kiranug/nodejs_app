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
                echo 'Deploying....'
            }
        }
    }
}
