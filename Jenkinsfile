pipeline {
    environment {
        IMAGEN = "josedom24/myapp"
        USUARIO = "paulmanosalvas1@gmail.com/Mega.2024"
    }
    agent any
    stages {
        stage('Clone') {
            steps {
                git branch: "main", url: 'https://github.com/katy8812/devops.git'
            }
        }
        stage('Build') {
            steps {
                script {
                    newApp = docker.build "$IMAGEN:$BUILD_NUMBER"
                }
            }
        } 
        stage('Deploy') {
            steps {
                script {
                    docker.withRegistry( 'https://hub.docker.com/', USUARIO ) {
                        newApp.push()
                    }
                }
            }
        }
    }
}
