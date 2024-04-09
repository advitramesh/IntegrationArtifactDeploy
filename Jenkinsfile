@Library('piper-lib-os') _

node() {
    stage('init') {
        deleteDir()
        checkout scm
    }
    stage('deployIntegrationArtifact Command') {
        try {
            // Your integrationArtifactDeploy step call
            integrationArtifactDeploy script: this

        } catch (Exception e) {
            // Logging the error message
            echo "Error during integrationArtifactDeploy: ${e.getMessage()}"
            
            // Re-throw the exception to mark the build as failed
            throw e
        }
    }
}
