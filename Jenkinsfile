pipeline {
    agent any

    stages {
        stage('Run Microservice A') {
            steps {
                script {
                    echo 'Triggering Microservice A Jenkins Job'
                    try {
                        def jobA = '/Cloud-Sheger-Modules/Packages/microservice-a-job'
                        if (Jenkins.instance.getItemByFullName(jobA)) {
                            build job: jobA, wait: true
                        } else {
                            error("Error: Microservice A job not found at path '${jobA}'")
                        }
                    } catch (Exception e) {
                        echo "Error: Microservice A job failed - ${e.message}"
                        error("Microservice A job failed, aborting pipeline.")
                    }
                }
            }
        }

        stage('Run Microservice B') {
            steps {
                script {
                    echo 'Triggering Microservice B Jenkins Job'
                    try {
                        def jobB = '/Cloud-Sheger-Modules/Packages/microservice-b-job'
                        if (Jenkins.instance.getItemByFullName(jobB)) {
                            build job: jobB, wait: true
                        } else {
                            error("Error: Microservice B job not found at path '${jobB}'")
                        }
                    } catch (Exception e) {
                        echo "Error: Microservice B job failed - ${e.message}"
                        error("Microservice B job failed, aborting pipeline.")
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