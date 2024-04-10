@Library('piper-lib-os') _

node() {
    stage('init') {
        deleteDir()
        checkout scm
    }
    stage('deployIntegrationArtifact Command') {
        withCredentials([string(credentialsId: 'sapcpidevServiceKeyCredentials', variable: 'PIPER_apiServiceKey')]) {

            integrationArtifactDeploy script: this
        }
    }
}
