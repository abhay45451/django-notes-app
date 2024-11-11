@Library("shared") _
pipeline {
    agent {
        label "node"
    }
    stages {
        stage("code") {
            steps {
                script{
                clone("https://github.com/abhay45451/django-notes-app.git","main")
            }
            }
        }
        stage("build") {
            steps {
                script{
                    docker_build("abhay45", "notesapp", "latest")
                }
            }
        }
        stage("docker_push") {
            steps {
                script{
                    docker_push("abhay45","notesapp","latest")
                }
            }
        }
        stage("deploy") {
            steps {
                echo "This is the deploy stage"
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
}
                
