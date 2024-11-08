pipeline {
    agent any
    stages {
        stage('Deploy'){
            steps{
                sh '''
                    cd ./zizzy-ops-multi-tier-app/
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
