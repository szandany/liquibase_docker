pipeline {
    agent {
        docker { image 'liquibase/liquibase:latest' }
    }
    stages {
        stage('Test') {
            steps {
                sh  '''
               echo "hello"
                '''
            }
        }
    }
}
