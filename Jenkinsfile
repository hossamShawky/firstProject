pipeline {
    agent any
    stages {
        stage('build') {
            script {
            
            steps {
            echo "Start Building:
                withCredentials([usernamePassword(credentialsId: '1af01033-0e90-4178-b9eb-f7abec0e3b22', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh '''
                       docker login -u $USERnAME -p PASSWORD
                       docker build -t hossam23/cd-cd1:v{BUILD_NUMBER}
                       docker push
                       
                       
                    '''
                }
            
            }
            }
        }
    }
}
