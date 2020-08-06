pipeline {
    agent any
    stages {
        stage ('mvn build') {
            steps {
                bat 'mvn clean package'
            }
            post {
                success {
                    echo 'Archiving Artifacts'
                    archiveArtifacts artifacts: '**/target/*.war'
                }                    
            }
        }
        stage ('Deploy to Staging') {
            steps {
                build job: 'deploy-to-staging'
            }
        }
        stage ('Deployment to Production') {
            steps {
                timeout (time:5, unit:'DAYS') {
                    input message: 'Approve production deployment'
                }

                build job: 'deploy-to-production'
            }

            post {
                success {
                    echo 'production deployment successfull'
                }

                failure {
                    echo 'production deployment failed'
                }
            }
        }
    }
}