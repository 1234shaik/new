pipeline {
    agent any

    stages {
        stage('Check Artifactory Reachability') {
            steps {
                script {
                    // Use bat or sh step to run curl command based on the Jenkins agent
                    def response
                    if (isUnix()) {
                        // Unix-like system (Linux)
                        response = sh(script: 'curl -s -o /dev/null -w "%{http_code}" http://localhost:8082/artifactory', returnStatus: true)
                    } else {
                        // Windows
                        response = bat(script: 'curl -s -o NUL -w "%{http_code}" http://localhost:8082/artifactory', returnStatus: true)
                    }

                    if (response == 200) {
                        echo 'Artifactory is reachable'
                    } else {
                        error 'Artifactory is not reachable'
                    }
                }
            }
        }

        // Other stages of your pipeline
    }
}
