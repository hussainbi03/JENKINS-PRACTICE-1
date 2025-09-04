pipeline {
    agent { label 'AGENT-1' }
        stages {
            stage ('build') {
                steps {
                    script {
                        sh """
                            echo "Hello, this is build"
                         """   
                    }
                }
            }
            stage ('test') {
                steps {
                    script {
                        sh """
                            echo "Hello, this is test"
                         """   
                    }
                }
            }
            stage ('deploy') {
                steps{
                    script {
                        sh """
                            echo "Hello, this is deploy"
                         """   
                    }
                }
            }
        }
        post {
            always{
                echo "I'll always say hello again"
            }
            success {
                echo "Pipeline is success"
            }
            failure {
                echo "Pipeline is failed"
            }
        }
    }
