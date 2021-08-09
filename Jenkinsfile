#!/usr/bin/env groovy
// Liquibase declarative pipeline
//
//
pipeline {
agent any
  environment {
    PATH="/usr/local/bin:$PATH"
    ENVIRONMENT_STEP="${params.'Pipeline Step'}"
  }
  stages {

    stage ('Precheck docker version') {
		steps {
			sh '''
        docker --version
			'''
		} // steps
	} // stage 'precheck'
  
  stage ('running liquibase with docker') {
      steps {
        // checkout Liquibase project from CLO repo
        sh '''
        . ~/exp_lb_env_vars_h2.sh
	cwd=$(pwd)
        docker run \
	--env LIQUIBASE_COMMAND_USERNAME \
	--env LIQUIBASE_COMMAND_PASSWORD \
	--env LIQUIBASE_COMMAND_URL \
	--env LIQUIBASE_PRO_LICENSE_KEY \
	--rm \
	-v "${cwd}"/changelogs:/liquibase/changelog:z \
	liquibase/liquibase:latest status --verbose
          
	  
	  
	 # docker run --rm -v "${cwd}"/changelogs:/liquibase/changelog:z liquibase/liquibase:latest --url="jdbc:h2:mem:liquibase_${ENVIRONMENT_STEP}" --changeLogFile=changeLog.h2.sql --username=admin --password=password updateSQL
         # docker run --rm -v "${cwd}"/changelogs:/liquibase/changelog:z liquibase/liquibase:latest --url="jdbc:h2:mem:liquibase_${ENVIRONMENT_STEP}" --changeLogFile=changeLog.h2.sql --username=admin --password=password --logLevel=debug update
	 # docker run --rm -v "${cwd}"/changelogs:/liquibase/changelog:z liquibase/liquibase:latest --url="jdbc:h2:mem:liquibase_${ENVIRONMENT_STEP}" --changeLogFile=changeLog.h2.sql --username=admin --password=password --logLevel=debug rollbackCount 1
          '''
      } // steps for checkout stages
    } // stage 'checkout'
    
  } // stages
}  // pipeline
