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
			'''
		} // steps
	} // stage 'precheck'
  
  stage ('running liquibase with docker') {
      steps {
        // checkout Liquibase project from CLO repo
        sh '''
          { set +x; } 2>/dev/null
          cwd=$(pwd)
          echo "Current workspace is ${cwd}"
          '''
      } // steps for checkout stages
    } // stage 'checkout'
    
  } // stages
}  // pipeline
