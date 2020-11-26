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

    stage ('Precheck docker version') {
		steps {
			sh '''
        { set +x; } 2>/dev/null
        docker --version
			'''
		} // steps
	} // stage 'precheck'
  } // stages
}  // pipeline
