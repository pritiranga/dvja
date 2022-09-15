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

            stage('Test') {
                steps {
                    sh 'make test'

                    script {
                        def testResults = findFiles(glob: 'build/reports/**/*.xml')
                        for(xml in testResults) {
                            touch xml.getPath()
                        }
                    }
                }
        }
 

            post {
                always {
                    archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
                    junit 'build/reports/**/*.xml'
                }
            }
            
        }
    }
    }
