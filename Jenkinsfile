pipeline {
    agent any
    stages {
        stage('build') {
            steps {
            echo "Start Building:
                withCredentials([usernamePassword(credentialsId: '1af01033-0e90-4178-b9eb-f7abec0e3b22', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh '''
                        echo "My username is $USERNAME"
                        echo "My password is $PASSWORD"
                    '''
                }
            }
        }
    }
}
