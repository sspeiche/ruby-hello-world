node('agent') {
  def project = "pipelineproject"

  stage 'Validate PR'
  echo 'Validating PR...'

  stage 'Build'
  def builder = new com.openshift.jenkins.plugins.pipeline.OpenShiftBuilder("", "ruby-sample-build", $project , "", "", "", "", "true", "", "")
  step builder

  stage 'Test'
  sh 'echo "Testing..." && sleep 30'

  stage 'Stage'
  def deployer = new com.openshift.jenkins.plugins.pipeline.OpenShiftDeployer("", "frontend", $project,"","")
  step deployer

  stage 'PreProd'
  sh 'echo "Promoting to pre-prod..." && sleep 30'
}
