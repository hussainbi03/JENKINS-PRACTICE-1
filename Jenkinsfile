pipeline {
    agent { label 'AGENT-1' }
    environment {
        PROJECT = "expense"
        COMPONENT = "backend"
    }
        stages {
            stage ('build') {
                steps {
                    script {
                        sh """
                            echo "Hello, this is build"
                            echo "the project is $PROJECT
                         """   
                    }
                }
            }
            stage ('test') {
                steps {
                    script {
                        sh """
                            echo "Hello, this is test"
                            echo " this is for $COMPONENT component
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
