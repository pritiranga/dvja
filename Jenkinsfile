    pipeline {
        agent any
        tools {
            maven 'Maven'
        }

        stages {
            stage('Build and test') {
                steps {
                    // Get some code from a GitHub repository
                    //checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/pritiranga/dvja.git']]])
                    // Run Maven on a Unix agent.
                    sh "mvn -Dmaven.test.failure.ignore=true clean install test"

                    // To run Maven on a Windows agent, use
                    // bat "mvn -Dmaven.test.failure.ignore=true clean install test"
                }

            post {
                 // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    junit(testResults: 'target/surefire-reports/*.xml', allowEmptyResults : true)
            
                    archiveArtifacts 'target/*.war'
                }
            }
            
        }
    }
