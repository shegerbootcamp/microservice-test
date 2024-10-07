pipeline {
    agent any

    stages {
        stage('Run Microservice A') {
            steps {
                script {
                    echo 'Triggering Microservice A Jenkins Job'
                    try {
                        build job: '/Cloud-Sheger-Modules/Packages/microservice-a-job', wait: true
                    } catch (Exception e) {
                        echo "Error: Microservice A job not found or failed - ${e.message}"
                        error("Microservice A job failed or not found, aborting pipeline.")
                    }
                }
            }
        }

        stage('Run Microservice B') {
            steps {
                script {
                    echo 'Triggering Microservice B Jenkins Job'
                    try {
                        build job: '/Cloud-Sheger-Modules/Packages/microservice-b-job', wait: true
                    } catch (Exception e) {
                        echo "Error: Microservice B job not found or failed - ${e.message}"
                        error("Microservice B job failed or not found, aborting pipeline.")
                    }
                }
            }
        }
    }

    post {
        success {
            echo 'Both Microservice A and B have been successfully deployed!'
        }
        failure {
            echo 'Pipeline failed during one of the microservice jobs'
        }
    }
}