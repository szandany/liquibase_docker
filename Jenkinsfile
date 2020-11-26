#!/usr/bin/env groovy
// Liquibase declarative pipeline
//
//
pipeline {
agent any
  environment {
    PATH="/usr/local/bin/docker:$PATH"
  }
  stages {

    stage ('Precheck docker version') {
		steps {
			sh '''
        { set +x; } 2>/dev/null
        docker --version
        echo "Current workspace is ${env.WORKSPACE}"
			'''
		} // steps
	} // stage 'precheck'
  
  stage ('running liquibase with docker') {
      steps {
        // checkout Liquibase project from CLO repo
        sh '''
          { set +x; } 2>/dev/null
          echo "Current workspace is ${env.WORKSPACE}"
          '''
      } // steps for checkout stages
    } // stage 'checkout'
    
  } // stages
}  // pipeline
