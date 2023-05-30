

pipeline {
    agent {label "lab2-node01"}

    stages {
        stage('Hello') {
            steps {
                echo 'CI/CD'
                sh '''
                echo " Project Files : "
                ls
                '''
            }
        }
    }
}
