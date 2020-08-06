pipeline {
    agent any
    stages {
        stage ("Build Docker Image") {
            steps {
                bat "mvn clean package"
                bat "docker build . -t tomcatwebapp:${env.build_number}"
                bat "docker run -d -p 880${env.build_number}:8080 tokcatwebapp:${env.build_number}"
            }
        }
    }
}