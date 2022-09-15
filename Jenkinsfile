    pipeline {
        agent any
        tools {
            maven 'Maven'
        }

        stages {
            stage('Build') {
                steps {
                    sh "mvn -Dmaven.test.failure.ignore=true clean install test"
                }
            }
            stage('Test') {
                steps {

                    script {
                        def testResults = findFiles(glob: 'build/reports/**/*.xml')
                        for(xml in testResults) {
                            touch xml.getPath()
                        }
                    }
                }
            }
        }

        post {
              always {
                  archiveArtifacts artifacts: 'build/libs/**/*.jar'
                  junit 'build/reports/**/*.xml'
                }
            }
            
        }
   
   
