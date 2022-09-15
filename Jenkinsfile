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
            stage('Package') {
                steps {
                sh(script: './mvnw --batch-mode package -DskipTests')
            }
        }
    }
        post {
            always {
                junit(testResults: 'target/surefire-reports/*.xml', allowEmptyResults : true)
            }
        }
    }
       
   
   
