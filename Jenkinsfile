    pipeline {
        agent any

        stages {
            stage('GitHub Cloning') {   
                steps {
                    sh '''
                    rm -rf Typescript-Docker-Jenkins
                    git clone git@github.com:boda175/Typescript-Docker-Jenkins.git
                    '''
                }
            }

            stage('Build') {
                steps {
                sh '''
                    cd Typescript-Docker-Jenkins/
                    docker image build -t node-ts -f Dockerfile-node .
                    '''
                }

            }

            stage('Deploy') {
                steps {
                    sh 'docker container run -p 5000:5100 -d node-ts '
                }
            }
        }
    }