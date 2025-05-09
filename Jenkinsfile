@Library("Shared") _
pipeline{
    
    agent {label "agent-vinod"}
    stages{
        stage("hello"){
            steps{
                script{
                    hello( )
                }
            }
        }
        stage("Code"){
          steps{
              script{
                  clone("https://github.com/usertan123/django-notes-app.git","dev")   
              }
          }  
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app", "latest", "tanmaytech")
                }
            }
        }
        stage("Push to Dockerhub"){
            steps{
                echo "This is pushing image to dockerhub"
                    docker_push("notes-app","latest","tanmaytech")
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker-compose down"
                //sh "docker run -d -p 8000:8000 notes-app:latest"
                sh "docker-compose up -d "
            }
        }
    }
}
