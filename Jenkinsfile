pipeline {
    agent { label "lab2-node01" }
    stages {
        stage('build') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-credentials', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    echo 'CI/CD'
                    sh '''
                        docker login -u $USERNAME -p $PASSWORD
                        docker build -t hossam23/demo:v${BUILD_NUMBER} .
                        docker push hossam23/demo:v${BUILD_NUMBER}
                        
                        echo "Your Img.V:${BUILD_NUMBER}"
                    '''
                }
            }
        }
    }
}
