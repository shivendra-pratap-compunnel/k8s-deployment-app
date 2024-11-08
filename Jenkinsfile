pipeline {
    agent any
    stages {
        stage('Deploy'){
            steps{
                sh '''
                    cd ./zizzy-ops-multi-tier-app/
                    helmfile sync
                    minikube service  --all
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
