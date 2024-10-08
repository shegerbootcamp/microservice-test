pipeline {
    agent any

    stages {
        stage('Run Microservice Jobs') {
            failFast true
            parallel {
                stage('Run Microservice A') {
                    steps {
                        echo 'Triggering Microservice A Jenkins Job'
                        // Handle branch name with slashes
                        script {
                           // def branchNameA = env.BRANCH_NAME.replace("/", "%2F")
                            build job: "../Packages/microservice-a-job", wait: true
                        }
                    }
                }

                stage('Run Microservice B') {
                    steps {
                        echo 'Triggering Microservice B Jenkins Job'
                        // Handle branch name with slashes
                        script {
                            //def branchNameB = env.BRANCH_NAME.replace("/", "%2F")
                            build job: "../Packages/microservice-b-job", wait: true
                        }
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