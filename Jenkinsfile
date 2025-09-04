pipeline {
    agent { label 'AGENT-1' }
    environment {
        PROJECT = "expense"
        COMPONENT = "backend"
        DEPLOY_TO = "production"
    }
    options {
        disableConcurrentBuilds()
        timeout(time : 30, unit: 'MINUTES')
    }
    parameters{
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
        stages {
            stage ('build') {
                steps {
                    script {
                        sh """
                            echo "Hello, this is build"
                            echo "the project is $PROJECT "
                            echo " hello ${params.PERSON}"
                             echo "Biography: ${params.BIOGRAPHY}"
                             echo "Toggle: ${params.TOGGLE}"
                             echo "Choice: ${params.CHOICE}"
                             echo "Password: ${params.PASSWORD}"
                            sleep 15
                         """   
                    }
                }
            }
            stage ('test') {
                steps {
                    script {
                        sh """
                            echo "Hello, this is test stage"
                            echo " this is for $COMPONENT component"
                         """   
                    }
                }
            }
            stage ('deploy') {
                input {
                    message "should we contunue?"
                    ok "yes, we can"
                    submitter "alice, bob"
                }
                when {
                    environment name: 'DEPLOY_TO', value: 'production'
                }
                steps{
                    script {
                        sh """
                            echo "Hello, this is deploy"
                         """   
                    }
                }
            }
        }
         stage('Parallel Stages') {
            parallel {
                stage('STAGE-1') {
                    
                    steps {
                        script{
                            sh """
                                echo "Hello, this is STAGE-1"
                                sleep 15
                            """
                        }
                    }
                }
                stage('STAGE-2') {
                    
                    steps {
                        script{
                            sh """
                                echo "Hello, this is STAGE-2"
                                sleep 15
                            """
                        }
                    }
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
    
