pipeline {
    agent 'any'
    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "Maven"
    }
    stages{
        stage('build') {
            steps {
                sh 'mvn clean install test -f pom.xml'
            }
        }


  }
  post {
    always {
      junit testDataPublishers: [attachments()], testResults: 'poc-dvja-script/target/test-reports/*.xml'
    }
  }
}
