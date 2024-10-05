pipeline {
    agent any

    stages {
        stage('Trigger Microservices') {
            parallel {
                stage('Trigger Microservice A') {
                    steps {
                        echo 'Triggering Microservice A Jenkins Job'
                        dir('microservice-a') {
                            build job: 'microservice-a-job', wait: true
                        }
                    }
                }

                stage('Trigger Microservice B') {
                    steps {
                        echo 'Triggering Microservice B Jenkins Job'
                        dir('microservice-b') {
                            build job: 'microservice-b-job', wait: true
                        }
                    }
                }
            }
        }
    }
}