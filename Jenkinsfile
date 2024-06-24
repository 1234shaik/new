pipeline {
    agent any

    environment {
        ARTIFACTORY_SERVER_ID = 'artifactory'
        ARTIFACTORY_URL = 'http://localhost:8081/artifactory'
        ARTIFACTORY_USERNAME = 'admin' // Default admin username
        ARTIFACTORY_PASSWORD = 'password' // Default admin password, change accordingly
        ARTIFACTORY_CREDENTIALS_ID = 'jfrog-password1'
    }
post {
        always {
            archiveArtifacts artifacts: 'spring-pet-frame/target/*.war', allowEmptyArchive: true
        }
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
