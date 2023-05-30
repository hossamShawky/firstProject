

pipeline {
    agent {label "lab2-node01"}

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
                sh '''
                ls
                '''
            }
        }
    }
}
