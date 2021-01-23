pipeline {
    agent any
            environment {
            DOCKER_REPO_NAME = 'pankaj2934'
            DOCKER_CRED = credentials('dockerhub')

            }
             stages {
                 stage ('dev') {
                 steps {
                  sh '''
                  docker login -u $DOCKER_CRED_USR -p $DOCKER_CRED_PSW
                  '''
                  }
                 }
                 stage ('test'){
                 steps {
                  sh '''
                  docker build . -t $DOCKER_REPO_NAME/$IMAGE_NAME:$IMAGE_VERSION.$BUILD_NUMBER
                  '''
                  }
                 }

                 stage ('prod'){
                 steps {
                  sh '''
                  docker push $DOCKER_REPO_NAME/$IMAGE_NAME:$IMAGE_VERSION.$BUILD_NUMBER
                  '''
                  }
                 }
             }

}
