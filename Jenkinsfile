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
    stage('Test') {
      steps {
        sh(script: './mvnw --batch-mode -Dmaven.test.failure.ignore=true test')

      }
    }

  }
  post {
    always {
      junit skipPublishingChecks: true, testResults: 'test-results.xml'
    }
  }
}
