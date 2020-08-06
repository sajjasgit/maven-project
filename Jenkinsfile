pipeline {
    agent any
    stages {
        stage ("Build Docker Image") {
            steps {
                bat "mvn clean package"
                bat "docker build . -t tomcatwebapp:${env.build_number}"
            }
        }
    }
}