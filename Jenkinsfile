    pipeline {
        agent any
        tools {
            maven 'Maven'
        }

        stages {
            stage('Build and test') {
                steps {
                    sh "mvn -Dmaven.test.failure.ignore=true clean install test"
                }

            post {
                 // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    junit skipPublishingChecks: true, testResults: 'test-results.xml'
            
                    archiveArtifacts 'target/*.war'
                }
            }
            
        }
    }
    }
