#!/usr/bin/env groovy

stage('build') {
    node {
      sh 'javac HelloWorld.java'
    }
}

stage name: 'wait a while', concurrency: 1
    node {
        sh 'sleep 1'
    }

stage('run') {
    parallel 'run': {
        node {
          sh 'java HelloWorld'
        }
    }, 'say something': {
        echo 'something'
    }
}
