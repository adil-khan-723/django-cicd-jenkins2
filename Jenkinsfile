pipeline {
    agent any

    triggers {
        pollSCM('* * * * *')
    }

    environment {
        DOCKER = credentials('DockerHub')
        IMAGE = 'notes-app'
    }

    stages {
        
        stage("code pull") {
            steps {
                echo "pulling code"
                git branch: 'main', url: 'https://github.com/adil-khan-723/django-cicd-jenkins2.git'
                echo "code pull successful"
            }
        }

        stage("build") {
            steps {
                echo "This is the build stage"
                sh 'docker build -t ${IMAGE} .'
            }
        }

        stage("push to dockerhub") {
            steps{
                echo "pushing the image to dockerhub"
                sh "docker login -u ${DOCKER_USR} -p ${DOCKER_PSW}"
                echo "login successful tagging the image ...."
                sh "docker image tag ${IMAGE}:latest ${DOCKER_USR}/${IMAGE}"
                echo "image tagged as: ${DOCKER_USR}/${IMAGE}"
                sh "docker push ${DOCKER_USR}/${IMAGE}"
            }
        }
    }
}