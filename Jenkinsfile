    pipeline {
        agent any
        tools {
            maven 'Maven'
        }

        stages {
            stage('Build and Unit test') {
        
                steps {
                    script {
                        module_Maven('clean verify')
                    }
                }
                post {
                    always {
                        junit testResults: '**/target/surefire-reports/*.xml', allowEmptyResults: false
                    }
                }
            }
        }
    }
