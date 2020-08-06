pipeline {
    agent any
    stages {
        stage ("Build Docker Image") {
            bat "mvn clean package"
            bat "docker build . -t tomcatwebapp:${env.buildID}"
        }
    }
}