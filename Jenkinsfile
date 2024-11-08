pipeline {
    agent any
    stages {
        stage('Deploy'){
            steps{
                sh '''
                    cd ./zizzy-ops-multi-tier-app/
                    helmfile sync
                    kubectl port-forward services/ui-helloworld 7878:5000 > /dev/null 2>&1 &
                '''
            }
        }
    }
    post {
	always{
	    cleanWs()
    	}
    }
}
