pipeline {
    agent any
    stages {
        stage ('mvn build') {
            steps {
                sh 'mvn clean package'
            }
            post {
                success:
                    echo 'Archiving Artifacts'
                    archiveArtifacts artifacts: '**/target/*.war', followSymlinks: false
            }
        }
        stage ('Deploy to Staging') {
            steps {
                build job: 'deploy-to-staging'
            }
        }
    }
}