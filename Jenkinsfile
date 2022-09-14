    pipeline {
        agent none
        tools {
            maven 'Maven'
        }

        stages {
            stage('Build and Unit test') {
                agent { label 'maven' }
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
