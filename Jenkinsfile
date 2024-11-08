pipeline {
    agent any
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
    }
}
