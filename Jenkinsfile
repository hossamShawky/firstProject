

pipeline {
    agent {label "lab2-node01"}

    stages {
        stage('build') {
            script {
             withCredentials([usernamePassword(credentialsId: 'docker-credentials', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
             steps {
                echo 'CI/CD'
                sh '''
                docker -u $USERNAME -p $PASSWORD
                 docker build -t hossam23/demo:v1 .
                 docker push
                 
                '''
            }
             }
            
            }
        }
    }
}
