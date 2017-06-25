#!/usr/bin/env groovy

stage('build') {
    node('a') {
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
        node('b') {
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

stage('mail') {
    def message = "Did a new local build. See: ${env.BUILD_URL}"
    echo "Sending mail:\n${message}"
//    mail body: message, subject: 'Jenkins build done', to: 'stefan_verhoeff@yahoo.com'
}
