pipeline {
    agent any

    stages {
        stage('Check Newman') {
            steps {
                sh 'node -v'
                sh 'npm -v'
                sh 'newman -v'
            }
        }

        stage('Run Postman Collection') {
            steps {
                sh '''
                newman run postman/DEMO-API.postman_collection.json \
			-e postman/SIT.postman_environment.json
                '''
            }
        }
    }
}