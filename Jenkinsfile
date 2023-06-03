pipeline {
    agent { label "lab2-node01" }
    stages {
        stage('build') {
            steps {
                if (BRANCH_NAME == "test" || BRANCH_NAME == "master") {
                    withCredentials([usernamePassword(credentialsId: 'docker-credentials', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                        echo 'CI/CD'
                        sh '''
                            docker login -u $USERNAME -p $PASSWORD
                            docker build -t hossam23/demo:v${BUILD_NUMBER} .
                            docker push hossam23/demo:v${BUILD_NUMBER}

                            echo "Your Img.V:${BUILD_NUMBER}"
                            echo "${BUILD_NUMBER}" > ../buildV.txt
                        '''
                    }
                }
                else {
                    echo "user choosed ${BRANCH_NAME}"
                }
            }
        }
        
        stage('deploy') {
            steps {
                if (BRANCH_NAME == "dev") {
                    withCredentials([file(credentialsId: 'kube-credentials', variable: 'KUBECONFIG')]) {
                        echo 'CI/CD'
                        sh '''
                            export BUILD_NUMBER=$(cat ../buildV.txt)
                            mv deploy.yaml deploy.yaml.tmp
                            cat deploy.yaml.tmp | envsubst > deploy.yaml
                            rm -f deploy.yaml.tmp

                            kubectl apply -f deploy.yaml --kubeconfig ${KUBECONFIG} -n ${BRANCH_NAME}
                            kubectl apply -f service.yaml --kubeconfig ${KUBECONFIG} -n ${BRANCH_NAME}
                        '''
                    }
                }
                else {
                    echo "Done......"
                }
            }
        }
    }
}
