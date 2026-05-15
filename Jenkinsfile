pipeline {
    agent any

    stages {

        stage('Install Newman') {
            steps {
                sh 'npm install -g newman'
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