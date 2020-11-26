pipeline {
    agent {
        docker { image 'liquibase/liquibase:latest' }
    }
    stages {
        stage('Test') {
            steps {
                sh 'liquibase/liquibase --version'
            }
        }
    }
}