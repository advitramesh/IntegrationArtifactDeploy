@Library('piper-lib-os') _

node() {
    stage('init') {
        deleteDir()
        checkout scm
    }
    stage('deployIntegrationArtifact Command') {
        // Assuming you have set CPI_FLOW_ID as a global environment variable
        withCredentials([string(credentialsId: 'sapcpidevServiceKeyCredentials', variable: 'PIPER_apiServiceKey')]) {
            // Retrieve the global variable and pass it to the integrationArtifactDeploy
            def flowId = env.Deploy_IntegrationFlowID
            integrationArtifactDeploy(script: this, integrationFlowId: flowId)
        }
    }
}
