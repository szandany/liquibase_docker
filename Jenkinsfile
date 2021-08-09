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
	--env LIQUIBASE_COMMAND_CHANGELOG_FILE \
	--rm \
	-v "${cwd}"/changelogs:/liquibase/changelog:z \
	liquibase/liquibase:latest status --verbose
        
        docker run \
	--env LIQUIBASE_COMMAND_USERNAME \
	--env LIQUIBASE_COMMAND_PASSWORD \
	--env LIQUIBASE_COMMAND_URL \
	--env LIQUIBASE_PRO_LICENSE_KEY \
	--env LIQUIBASE_COMMAND_CHANGELOG_FILE \
	--rm \
	-v "${cwd}"/changelogs:/liquibase/changelog:z \
	liquibase/liquibase:latest --log-level=info update
	
	docker run \
	--env LIQUIBASE_COMMAND_USERNAME \
	--env LIQUIBASE_COMMAND_PASSWORD \
	--env LIQUIBASE_COMMAND_URL \
	--env LIQUIBASE_PRO_LICENSE_KEY \
	--env LIQUIBASE_COMMAND_CHANGELOG_FILE \
	--rm \
	-v "${cwd}"/changelogs:/liquibase/changelog:z \
	liquibase/liquibase:latest history
          '''
      } // steps for checkout stages
    } // stage 'checkout'
    
  } // stages
}  // pipeline
