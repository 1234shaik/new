pipeline {
    agent any

    environment {
        ARTIFACTORY_SERVER_ID = 'artifactory'
        ARTIFACTORY_URL = 'http://localhost:8082/artifactory'
        ARTIFACTORY_CREDENTIALS_ID = 'jfrog-password1' // ID of the stored credentials in Jenkins
    }

    stages {
        stage('Check Connection') {
            steps {
                script {
                    def rtServer = Artifactory.server(ARTIFACTORY_SERVER_ID)
                    rtServer.url = ARTIFACTORY_URL
                    rtServer.credentialsId = ARTIFACTORY_CREDENTIALS_ID
                    rtServer.timeout = 300

                    // Attempt to ping the server
                    def response = rtServer.ping()
                    if (response) {
                        echo 'Successfully connected to JFrog Artifactory.'
                    } else {
                        error 'Failed to connect to JFrog Artifactory.'
                    }
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
