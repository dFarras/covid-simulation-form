def image_name = "covid-simulation-front-image"
def container_name = "simulation-front-container"
pipeline {
    agent httpd:2.4
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
