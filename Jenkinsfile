@Library("shared") _
pipeline{
    agent any
    stages{
        stage("hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("code"){
            steps{
                script{
                clone("https://github.com/gitvishalgit/django-notes-app.git","main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app","latest","vg1995")
                }
            }
        }
        stage("Push to Dockerhub"){
            steps{
                echo "This is pushing image."
                script{
                   docker_push("notes-app","latest","vg1995") 
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "this is deploying the code."
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
