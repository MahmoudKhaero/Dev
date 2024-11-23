pipeline {
    agent { label 'dev' }
    stages {
        stage('Build and Push Docker Image') {
            steps {
                  withCredentials([usernamePassword(credentialsId: 'dockerid', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh '''
                    docker build -t ${USER}/nextjs -f Dockerfile .
                    docker login -u ${USER} -p ${PASS}
                    docker push ${USER}/nextjs
                    '''
                  }
            }
        }   
    }
}
