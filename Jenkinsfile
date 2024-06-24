pipeline {
    agent any

    stages {
        stage('Check Artifactory Reachability') {
            steps {
                script {
                    def response = sh(script: 'curl -s -o /dev/null -w "%{http_code}" http://localhost:8082/artifactory', returnStdout: true).trim()
                    if (response == '200') {
                        echo 'Artifactory is reachable'
                    } else {
                        echo 'Artifactory is not reachable. HTTP Status Code: ' + response
                    }
                }
            }
        }
    }
}
