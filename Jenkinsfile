@Library("Shared") _
pipeline{
    agent{label "sanjana"}
    stages{
        stage('hello'){
            steps{
                hello()
            }
        }
        stage("Code"){
           steps{
               clone("https://github.com/Sanjana321/django-notes-app.git","dev")
           } 
        }
        stage("Build"){
           steps{
               script{
                 build("notes-app","latest","dubeysanjana")
               }  
           }
        }
        stage("Push to DockerHub"){
          steps{
             docker_push("notes-app","latest","dubeysanjana")
          }  
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose up -d"
            }
        }
    }
}
