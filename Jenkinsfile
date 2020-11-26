pipeline {
    agent {
        docker { image 'liquibase/liquibase' }
    }
    stages {
        stage('Test') {
            steps {
                sh 'liquibase/liquibase --version'
            }
        }
    }
}
