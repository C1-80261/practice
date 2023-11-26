pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/C1-80261/practice.git'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_p3jYrxxLOa_ZepweHHBzo_zTS8A | /usr/bin/docker login -u rutvijapatil --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker image build -t rutvijapatil/web11 .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push rutvijapatil/web11'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/bin/docker service rm myservice'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --name myservice -p 9090:80 --replicas 5 rutvijapatil/web11'
            }
        }
    }
}
