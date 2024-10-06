pipeline {
    agent any

    stages {
        stage('Run Microservice A') {
            steps {
                echo 'Triggering Microservice A Jenkins Job'
                build job: '/Cloud-Sheger-Modules/Packages/microservice-a-job', wait: true
            }
        }

        stage('Run Microservice B') {
            steps {
                echo 'Triggering Microservice B Jenkins Job'
                build job: '/Cloud-Sheger-Modules/Packages/microservice-b-job', wait: true
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