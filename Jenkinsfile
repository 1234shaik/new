pipeline {
    agent any

    stages {
        stage('Declarative: Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Check Artifactory Reachability') {
            steps {
                script {
                    def response
                    if (isUnix()) {
                        response = sh(script: 'curl -s -o /dev/null -w "%{http_code}" http://localhost:8082/artifactory', returnStatus: true)
                    } else {
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

        // Add more stages as needed
    }
}
