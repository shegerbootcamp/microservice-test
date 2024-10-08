pipeline {
    agent any

    stages {
        stage('Run Microservice Jobs') {
                stage('Run Microservice A') {
                    steps {
                        echo 'Sanitizing branch name for Microservice A'
                        script {
                            def branchNameA = env.BRANCH_NAME.replace("/", "%2F")
                            echo "Branch name for Microservice A: ${branchNameA}"
                            retry(3) {
                                build job: "../../Packages/microservice-a-job/${branchNameA}", wait: true
                            }
                        }
                    }
                }

                stage('Run Microservice B') {
                    steps {
                        echo 'Sanitizing branch name for Microservice B'
                        script {
                            def branchNameB = env.BRANCH_NAME.replace("/", "%2F")
                            echo "Branch name for Microservice B: ${branchNameB}"
                            retry(3) {
                                build job: "../../Packages/microservice-b-job/${branchNameB}", wait: true
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