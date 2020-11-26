pipeline {
    agent {
        docker { image 'liquibase/liquibase:latest' }
    }
    environment {
        PATH="/usr/local/bin/docker:$PATH"
  }
    stages {
        stage('Test') {
            steps {
                sh 'liquibase/liquibase --version'
            }
        }
    }
}
