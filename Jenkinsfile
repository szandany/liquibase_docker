#!/usr/bin/env groovy
// Liquibase declarative pipeline
//
//
pipeline {
agent any
  environment {
    PATH="/usr/local/bin:$PATH"
    ENVIRONMENT_STEP="${params.Pipeline Step}"
  }
  stages {

    stage ('Precheck docker and Liquibase version') {
		steps {
			sh '''
        # { set +x; } 2>/dev/null
        docker --version
			'''
		} // steps
	} // stage 'precheck'
  
  stage ('running liquibase with docker') {
      steps {
        // checkout Liquibase project from CLO repo
        sh '''
          # { set +x; } 2>/dev/null
          cwd=$(pwd)
          docker run --rm -v "${cwd}"/changelogs:/liquibase/changelog liquibase/liquibase:latest --url="jdbc:h2:mem:liquibase_${ENVIRONMENT_STEP}" --changeLogFile=changelog/changeLog.h2.sql --username=admin --password=password status --verbose
          docker run --rm -v "${cwd}"/changelogs:/liquibase/changelog liquibase/liquibase:latest --url="jdbc:h2:mem:liquibase_${ENVIRONMENT_STEP}" --changeLogFile=changelog/changeLog.h2.sql --username=admin --password=password updateSQL
          docker run --rm -v "${cwd}"/changelogs:/liquibase/changelog liquibase/liquibase:latest --url="jdbc:h2:mem:liquibase_${ENVIRONMENT_STEP}" --changeLogFile=changelog/changeLog.h2.sql --username=admin --password=password --logLevel=debug update
          '''
      } // steps for checkout stages
    } // stage 'checkout'
    
  } // stages
}  // pipeline
