def image_name = "simulation-form-image"
def container_name = "simulation-form-cntr"
pipeline {
    agent any
    stages {
        stage('KILL-PREV') {
            steps {
                sh "docker stop ${container_name} || true"
                sh "docker rm ${container_name} || true"
                sh "docker rmi ${image_name} || true"
            }
        }
        stage('DOCKER-BUILD') {
            steps {
                sh "docker build -t ${image_name} ."
                sh "docker run -d -p 80:80 --name=${container_name} ${image_name}"
            }
        }
    }
}
