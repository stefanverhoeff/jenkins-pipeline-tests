#!/usr/bin/env groovy

stage 'build'

node {
  sh 'javac HelloWorld.java'
}

stage 'run'

node {
  sh 'java HelloWorld'
}
