@Library('piper-lib-os') _

node() {
  stage('init') {
    deleteDir()
    checkout scm
  }
  stage('prepare piper') {
    dockerExecuteOnKubernetes(script: this, dockerImage: 'golang:1.15') {
      sh """|#!/bin/bash -e
            |git clone -b IntegrationArtifactFixes https://github.com/mayurmohan/jenkins-library piperlib
            |cd piperlib
            |go build -o piper .
            |mv piper ..
            |cd -
            |rm -rf piperlib
         """.stripMargin()
      stash name: 'piper-bin', includes: 'piper'
      sh "rm piper"
       
    }
  }
  stage('integrationArtifactGetServiceEndpoint Command') {
	  	setupCommonPipelineEnvironment script: this
	  	print "status:"
		integrationArtifactGetServiceEndpoint script: this
	  	print  commonPipelineEnvironment.getValue("iFlowServiceEndpoint")
  }
}
