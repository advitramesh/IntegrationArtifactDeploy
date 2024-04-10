@Library('piper-lib-os') _

node() {
    stage('init') {
        deleteDir()
        checkout scm
    }
    stage('deployIntegrationArtifact Command') {
        // Use the withCredentials to inject the service key into an environment variable
        withCredentials([string(credentialsId: 'sapcpidevServiceKeyCredentials', variable: 'PIPER_apiServiceKey')]) {
            // Assuming you have set CPI_FLOW_ID as a global environment variable
            // Access it using the env global variable in Jenkins
            def flowId = env.Deploy_IntegrationFlowID

            // Echoing the flowId for debugging purposes
            echo "Integration Flow ID: ${flowId}"
            
            // Pass the flowId to the integrationArtifactDeploy step
            integrationArtifactDeploy(script: this, integrationFlowId: flowId)
        }
    }
}
