#!/usr/bin/env groovy

stage('build') {
    node {
      sh 'javac HelloWorld.java'
      stash includes: 'HelloWorld.class', name: 'class'
    }
}

stage name: 'wait a while', concurrency: 1
    node {
        sh 'sleep 1'
    }

stage('run') {
    parallel 'run': {
        node {
            unstash 'class'
            sh 'ls -la'
            sh 'java HelloWorld'
        }
    }, 'say something': {
        node {
            echo 'something'
        }
    }
}
