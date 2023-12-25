pipeline {
    agent any
    
    stages{
        stage("Code") {
            steps{
                git url: "https://github.com/thisisyatingarg/Docker-two-tier-app.git", branch:"master"
            }
        }
        stage("Build or Test") {
            steps{
                sh "docker build . -t flaskapp"
            }
        }
        stage("Push to Repository") {
            steps{
                withCredentials([usernamePassword(credentialsId:"dockerhub", passwordVariable:"dockerhubPass", usernameVariable:"dockerhubUser")]) {
                    sh "docker login -u ${env.dockerhubUser} -p ${env.dockerhubPass}"
                    sh "docker tag flaskapp ${env.dockerhubUser}/flaskapp:latest"
                    sh "docker push ${env.dockerhubUser}/flaskapp:latest"
                }
            }
        }
        stage("Deploy") {
            steps{
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
}

