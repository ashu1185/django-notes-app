@Library("Shared-library") _    
pipeline{
    agent { label "jenkins-agent" }
    
    stages{
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
                script{
                    clone("https://github.com/ashu1185/django-notes-app.git", "main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app","latest","ashu1185")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app","latest","ashu1185")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is Deploying the code"
                sh "docker compose up -d"
            }
        }
    }
}
