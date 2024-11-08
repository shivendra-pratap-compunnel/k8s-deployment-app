pipeline {
    agent any
    tools {
        nodejs 'NodeJS_18'
    }
    environment {
        ORG_NAME = "eximius"
	    AKS_NAME = "eximius-aks"
        DEPLOYMENT_ENVIRONMENT = getEnvName(env.BRANCH_NAME)
        SERVICE_NAME = getservicename(env.GIT_URL.replaceFirst(/^.*\/([^\/]+?).git$/, '$1'))
        GITLEAKS='/var/lib/jenkins/external_tools/gitleaks/8.18.0'
        SONAR=credentials("sonar-token")
        scannerHome = tool 'SonarScanner-msbuild'
        BASTIONIP = '172.191.43.220'
        BASTIONUSER = 'eximius'
        GIT_COMMIT_SHORT = sh(
                script: "printf \$(git rev-parse --short ${GIT_COMMIT})",
                returnStdout: true
        )
    }

    stages {

        stage('SCM') {
            steps {
                git branch: 'main', url: 'git@github.com:shivendra-pratap-compunnel/k8s-deployment-app.git'
            }
        }

        stage('Deploy'){
            steps{
                sh '''
                    cd ./k8s-deployment-app/zizzy-ops-multi-tier-app/
                    helmfile sync
                '''
            }
        }
    }
    post {
	always{
	    cleanWs()
    	}
       //  success {
       //      office365ConnectorSend color: '#008000',message: "$BUILD_NUMBER - v$GIT_COMMIT_SHORT deployed successfully!)",status: "Success", webhookUrl: "${Velocity_WEB_HOOK_URL}"
       // }
       // failure {
       //     office365ConnectorSend color: '#FF0000',message: "$BUILD_NUMBER - v$GIT_COMMIT_SHORT deployment failed!)",status: 'Failed', webhookUrl: "${Velocity_WEB_HOOK_URL}"
       // }
    }
}


