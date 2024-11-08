pipeline {
    agent any
    stages {
        stage('Deploy'){
            steps{
                sh '''
                    cd ./k8s-deployment-app/zizzy-ops-multi-tier-app/
                    helmfile sync
                '''
            }
        }
    }
    // post {
	// always{
	//     cleanWs()
    // 	}
    // }
}
