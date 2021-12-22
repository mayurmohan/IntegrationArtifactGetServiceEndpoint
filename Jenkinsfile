@Library('piper-lib-os') _

node() {
  stage('init') {
    deleteDir()
    checkout scm
  }
  stage('integrationArtifactGetServiceEndpoint Command') {
	  	setupCommonPipelineEnvironment script: this
	  	print "status:"
		integrationArtifactGetServiceEndpoint script: this
	  	print  commonPipelineEnvironment.getValue("custom/integrationFlowServiceEndpoint")
  }
}
