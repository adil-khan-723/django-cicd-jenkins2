pipeline {
    agent any

    triggers {
        pollSCM('* * * * *')
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
            echo "This is the build stage"
            sh 'docker build -t notes-app .'
        }

        
    }
}