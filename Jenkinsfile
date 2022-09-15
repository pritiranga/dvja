    pipeline {
        agent any
        tools {
            maven 'Maven'
        }

        stages {
            stage('Build') {
                steps {
                    sh "mvn -Dmaven.test.failure.ignore=true clean compile test"
                }
            }
        }
        post {
            always {
                junit(testResults: 'target/surefire-reports/*.xml', allowEmptyResults : true)
            }
        }
    }
       
   
   
