@Library('piper-lib-os') _

node() {
    stage('init') {
        deleteDir()
        checkout scm
    }
    stage('deployIntegrationArtifact Command') {
        script {
            // Read the configuration from the .yml file
            def config = readYaml file: './.pipeline/config.yml'

            // Log the loaded configuration for debugging
            echo "Loaded configuration: ${config}"
            
            // Extract the integrationFlowId from the config file
            def flowId = config.steps.integrationArtifactDeploy.integrationFlowId

            // Echoing the flowId for debugging purposes
            echo "Integration Flow ID: ${flowId}"
            
            // Use the credentialId from the config file
            def credentialsId = config.steps.integrationArtifactDeploy.cpiApiServiceKeyCredentialsId

            // Now use these values in the withCredentials and integrationArtifactDeploy steps
            withCredentials([string(credentialsId: credentialsId, variable: 'PIPER_apiServiceKey')]) {
                integrationArtifactDeploy(script: this, integrationFlowId: flowId)
            }
        }
    }
}
