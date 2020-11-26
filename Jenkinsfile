#!/usr/bin/env groovy
// Liquibase declarative pipeline
//
//
pipeline {
agent any
  environment {
    PATH="/usr/local/bin:$PATH"
  }
  stages {

    stage ('Precheck docker and Liquibase version') {
		steps {
			sh '''
        { set +x; } 2>/dev/null
        docker --version
	docker run --rm liquibase/liquibase:latest --version
			'''
		} // steps
	} // stage 'precheck'
  } // stages
}  // pipeline
